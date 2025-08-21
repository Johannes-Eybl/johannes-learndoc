#angular 
#JavaScript 
#frontend 
# Setup
Um Http-Requests zu verwenden, muss man der Applikation einen HttpClient zur Verfügung stellen.
In 'main.ts' muss man darum aus:
```TypeScript
bootstrapApplication(AppComponent).catch((err) => console.error(err));
```
die folgende Line machen:
```TypeScript
bootstrapApplication(AppComponent, {  
  providers: [provideHttpClient()]  
}).catch((err) => console.error(err));
```
Nun kann man den HttpClient in seine Components injecten:
```TypeScript
private httpClient = inject(HttpClient)
```

Zusätzlich zum HttpClient braucht man für Http-Requests noch ein 'DestroyRef'. Es ermöglicht das Aufrufen einer Funktion, wenn der Component zerstört wird. Es wird verwendet, um die Subscription beim HttpClient abzumelden.(selectPlace)="onSelectPlace($event)"
# Outsourcen von Requests in einem Service
Anstatt ganze Requests innerhalb von einem einzigen Component zu erstellen, macht es mehr Sinn, Requests teilweise auf einen Service auszulagern. 

Üblicherweise hat man die Subscription innerhalb von dem Component, der die Daten verarbeitet. Dadurch kann man die Subscription auch beim Zerstören des Components beenden (ein Service würde nicht wissen, ob der Component zerstört wurde).
Die Konfiguration der Requests hingegen schreibt man innerhalb von einem Service, 

Beispielsweise hätte man innerhalb vom Service folgenden Code, der die Request macht: 
```TypeScript
private fetchPlaces(url: string) {  
  return this.httpClient  
    .get<{ places: Place[] }>(url)  
}
```
und innerhalb vom Component würde man den Service auf folgende Weise ansprechen: 
```TypeScript
ngOnInit() {  
  this.isFetching.set(true)  
  const subscription = this.placeService.loadAvailablePlaces().subscribe({  
      next: (resData) => {  
        this.places.set(resData.places)  
      },  
      error: (err) => {  
        console.error(err.message)  
        this.error.set("Unknown error")  
      },  
      complete: () => {  
        this.isFetching.set(false)  
      }  
    })  
  
  this.destroyRef.onDestroy(() => {  
    subscription.unsubscribe()  
  })  
}
```
Die Interaktion mit dem [[Observable]] wird also zu 100% innerhalb des Components abgewickelt. Nur die Anfrage an sich wird innerhalb vom Service gemacht.
# Der HttpClient
HttpClient enthält sämtliche REST-Anfragen, die man zu einer API machen muss. Er ist ein [[Observable]] und muss darum mit den drei [[Observable]]-Methoden 'next', 'error' und 'complete' ausgestattet werden.
## GET
Im folgenden Beispiel befindet sich die GET-Methode innerhalb von der 'ngOnInit'-Funktion. Bei vielen Anwendungsfällen muss man beim Laden einer Seite die Daten aus dem Backend fetchen, wie es hier der Fall ist.
```TypeScript
@Component({ .. })
export class AvailablePlacesComponent implements OnInit {  
  places = signal<Place[] | undefined>(undefined);  
  
  private httpClient = inject(HttpClient)  
  private destroyRef = inject(DestroyRef)  
  
  ngOnInit() {  
    const subscription = this.httpClient  
      .get<{ places: Place[] }>('http://localhost:3000/places')  
      .subscribe({  
        next: (resData) => {  
          this.places.set(resData.places)  
        }  
      })  
  
    this.destroyRef.onDestroy(() => {  
      subscription.unsubscribe()  
    })  
  }  
}
```
## PUT
```TypeScript
this.httpClient.put('http://localhost:3000/user-places', {  
  placeId: selectedPlace.id  
}).subscribe({  
    next: (responseData) => {  
      console.log(responseData)  
    }  
  }  
)
```
### Optimistic Updating
Häufig will man, wenn man etwas auf dem Server speichert, diese Daten möglichst schnell auch im Frontend anzeigen. Beispielsweise will man ein Like schon zählen, auch wenn das Backend dieses noch gar nicht erhalten hat.

Dieses Verhalten nennt man optimistic updating - man ändert die Oberfläche, bevor der Server die Änderung bestätigt. Natürlich muss man die Änderung auch zurücksetzen, wenn der Server einen Fehler ausgibt.
```TypeScript
@Injectable({ .. })  
export class PlacesService {  
  private userPlaces = signal<Place[]>([]);  
  private httpClient = inject(HttpClient);  
  
  addPlaceToUserPlaces(place: Place) {  
    const prevPlaces = this.userPlaces()  
  
    if (!prevPlaces.some(p => p.id === place.id)){  
      this.userPlaces.set([...prevPlaces, place])  
    }  
  
    return this.httpClient.put('http://localhost:3000/user-places', {  
      placeId: place.id  
    }).pipe(  
      catchError(err => {  
        this.userPlaces.set(prevPlaces)  
        return throwError(() => new Error('Error adding place to user places'))  
      })  
    )  
  }   
}
```
In dieser Funktion wird der State zwischengespeichert, bevor er manipuliert wird. So kann in der Funktion 'catchError' der State zurückgesetzt werden.
## DELETE
```TypeScript
return this.httpClient.delete('http://localhost:3000/user-places/' + place.id)  
  .pipe(  
    catchError((error) => {  
      this.userPlaces.set(prevPLaces)  
      this.errorService.showError('Failed to remove the selected place.')  
      return throwError(  
        () => new Error('Failed to remove the selected place.'))  
    })  
  )
```
Diese Funktion sendet eine DELETE-Request zum Server. Die Id des Objekts, das gelöscht werden soll wird in diesem Fall mit der URL mitgegeben.
# Error-Handling
Um einen Error zu verarbeiten, muss man in der 'subscribe'-Methode der httpClient-Subscription eine 'error'-Funktion hinzufügen. 
```TypeScript
ngOnInit() {  
  const subscription = this.httpClient  
    .get<{ places: Place[] }>('http://localhost:3000/places')  
    .subscribe({  
      next: (resData) => {  
        this.places.set(resData.places)  
      },  
      error: (err) => {  
        this.error.set(err.message || "Unknown error")  
      }
    })  
  
  this.destroyRef.onDestroy(() => {  
    subscription.unsubscribe()  
  })  
}
```
In der Funktion, die beim 'error'-Block definiert ist, wird dieser verarbeitet. In diesem Beispiel gibt es ein Signal, dessen Wert nun die Error-Message ist.
Im Html könnte man den Error nun folgendermassen anzeigen:
```HTML
 @if (error()) {  
  <p>An error occurred: {{ error() }}</p>  
}
```
# Fetch-Fallback
Häufig will man einen Fallback zeigen, wenn die Daten noch nicht geladen sind. 
In Angular ist das sehr einfach mit einem 'isFetching'-Signal erreichbar.

Dieses Signal wird am Start von 'ngOnInit' auf 'true' gesetzt und am Schluss der Funktion ('complete') auf 'false' gesetzt. 
```TypeScript
@Component({})  
export class AvailablePlacesComponent implements OnInit {  
  places = signal<Place[] | undefined>(undefined);  
  isFetching = signal(false);  
  
  private httpClient = inject(HttpClient)  
  private destroyRef = inject(DestroyRef)  
  
  ngOnInit() {  
    this.isFetching.set(true)  
  
    const subscription = this.httpClient  
      .get<{ places: Place[] }>('http://localhost:3000/places')  
      .subscribe({  
        next: (resData) => {  
          this.places.set(resData.places)  
        },  
        complete: () => {  
          this.isFetching.set(false)  
        }  
      })  
  
    this.destroyRef.onDestroy(() => {  
      subscription.unsubscribe()  
    })  
  }  
}
```
Nun kann man im Html mit '@if' abfragen, ob die Daten schon da sind: 
```HTML
@if(isFetching()){  
  <p class="fallback-text">Loading...</p>  
}
```
# HTTP-Interceptors
Angular erlaubt sogenannte HTTP-Interceptors. Das sind Funktionen, die kurz bevor oder kurz nach dem Senden von HTTP-Requests getriggert werden.

Um Interceptors zu aktivieren, muss man zu der Methode 'bootstrapApplication' in 'main.ts' den folgenden Parameter hinzufügen:
```TypeScript
  
bootstrapApplication(AppComponent, {  
  providers: [provideHttpClient(  
    withInterceptors([loggingInterceptor])  
  )]  
}).catch((err) => console.error(err));
```
In dem Array, das 'withInterceptors' mitgegeben wird, kann man die Funktionen, welche vor oder nach dem Senden von Http-Requests ausgelöst werden sollen, angeben.
In diesem Fall ist das nur die folgende Funktion:
```TypeScript
function loggingInterceptor(request: HttpRequest<unknown>, next: HttpHandlerFn) {  
  const req = request.clone({  
    headers: request.headers.set('DEBUG', 'TESTING'),  
  })  
  console.log("Outgoing request:" + request);  
  return next(request)  
}
```
Diese Funktion fügt der Request einen neuen header hinzu, druckt die Request in der Konsole aus und sendet sie danach weiter.
So könnte man eine Request manipulieren, bevor sie den Server erreicht.
## Nur auf bestimmte Events reagieren
Die Interceptor-Funktion im vorherigen Abschnitt wird bei jeder Http-Request getriggert. Will man nur auf bestimmte Requests reagieren, muss man die gleiche Funktion auf folgende Weise schreiben:
```TypeScript
function loggingInterceptor(request: HttpRequest<unknown>, next: HttpHandlerFn) {  
  return next(request).pipe(  
    tap({  
      next: event => {  
        if(event.type === HttpEventType.Response){  
          console.log("Received response");  
          console.log(event.status)  
        }  
      }  
    })  
  )  
}
```
So kann man abfragen, um welche Art von Http-Event es sich handelt und somit nur auf bestimmte Events reagieren.