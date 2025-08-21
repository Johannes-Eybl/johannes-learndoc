#JavaScript #frontend #angular 
# Was ist Routing
Angular-Applikationen sind meistens Single Page Applikationen - sie existieren nur auf einer einzigen Seite. Das bedeutet, dass es nur eine einzige HTML-Page gibt, welche mit Daten und [[Component]]s gefüllt ist. 

Anstatt verschiedene Screens mit Modals darzustellen, will man seine Applikation vielleicht auf verschiedene Pages verteilen, sodass eine Struktur von verschiedenen HTML-Pages ergibt ("/home", "/login", "/task" usw.).
# Routing in Angular konfigurieren
Um Routing in der eigenen Angular-Applikation zu ermöglichen, muss man die Datei 'main.ts' folgendermassen verändern:
```TypeScript
bootstrapApplication(AppComponent, {  
  providers: [provideRouter()]  
}).catch((err) => console.error(err));
```
Mit der Funktion 'provideRouter()' gibt man an, welche Routes (URLs) es innerhalb der Applikation geben soll. Diese Routes müssen aber als Parameter angegeben werden - der Code im Beispiel würde einen Fehler ausgeben:
```TypeScript 
bootstrapApplication(AppComponent, {  
  providers: [provideRouter([  
    {  
      path: 'tasks',  
      component: TasksComponent,  
    }  
  ])]  
}).catch((err) => console.error(err));
```
Nun wurde der Funktion 'provideRouter()' eine Liste von Konfigurationsobjekten gegeben, welche die möglichen Routes der Applikation definieren. Jedes Konfigurationsobjekt muss die folgenden Werte haben:
- path -> Unter welchem Path die Route auffindbar sein soll (hier "/tasks")
- component -> Welcher Component bei dem Pfad aufgerufen werden soll

> [!WARNING] Routes werden zur Übersicht meistens ausgelagert!

Da eine grosse Angular-Applikation häufig viele Routes haben kann, werden diese gerne in eine separate Datei ausgelagert ("app.routes.ts"):
```TypeScript
export const routes: Routes = [  
  {  
    path: 'tasks',  
    component: TasksComponent  
  },  
]
```
Diese Routes können dann im 'main.ts' importiert werden:
```TypeScript
bootstrapApplication(AppComponent, {  
  providers: [  
    provideRouter(routes)  
  ]  
}).catch((err) => console.error(err));
```
Bei grossen Projekten will man die [[#Routing-Konfiguration auf mehrere Dateien ausweiten]]!
# Routing-Konfiguration auf mehrere Dateien ausweiten
Bei grossen Projekten macht es Sinn, die verschiedenen Routes nicht in einer grossen Datei zu konfigurieren und stattdessen mehrere kleine Konfigurationsdateien zu erstellen.
```TypeScript
export const routes: Routes = [  
  {  
    path: '',  
    component: NoTaskComponent,  
  },  
  {  
    path: 'users/:userId',  
    component: UserTasksComponent,  
    children: [  
      {  
        path: 'tasks',  
        component: TasksComponent,  
      }  
    ]  
  },  
]
```
Wenn man dem Path 'users/:userId' noch mehr Kinder hinzufügen will, sollte man diese in einer anderen Datei definieren. 
```TypeScript
export const userRoutes: Routes = [
	{
		path: 'tasks',
		component: TasksComponent,
	}
]
```
Die Konfiguration der Kinder kann man dann in der anderen Datei importiert werden:
```TypeScript
export const routes: Routes = [  
  {  
    path: '',  
    component: NoTaskComponent,  
  },  
  {  
    path: 'users/:userId',  
    component: UserTasksComponent,  
    children: userRoutes  
  },  
]
```
# Daten zur Routing-Konfiguration hinzufügen - Route-Parameter
## Statische Daten mit 'data'
Man kann (unter anderem, denn es gibt viele Attribute, die es haben kann) dem Routing-Konfigurationsobjekt das Attribut 'data' hinzufügen. Diese Attribut hat als Wert ein Objekt, welches alle beliebigen Daten als Values für die eigenen Attribute speichern kann: 
```TypeScript
{  
  path: 'users/:userId',  
  component: UserTasksComponent,  
  children: userRoutes,  
  data: {  
    message: 'Hello'  
  }
}
```
In diesem Beispiel wird ein Konfigurationsobjekt auf dem Abschnitt [[#Routing-Konfiguration auf mehrere Dateien ausweiten]] genutzt.

Wenn in der Routing-Konfig ([[#Routing in Angular konfigurieren]]) die Option 'withComponentInputBinding()' aktiviert ist, kann man auf jedes Attribut des 'data'-Objekts als Input zugreifen. Das geht aber nur von dem Component aus, der im Konfigurationsobjekt mit diesem Path verbunden ist - in diesem Fall der 'userTasksComponent'.
```TypeScript
message = input.required<string>();
```
Da das Attribut 'message' in diesem Fall hardcoded ist, kann man beim Abfragen mit 'input' auch noch 'required' verwenden.
## Dynamische Daten mit 'resolve'
Will man innerhalb vom Konfigurationsobjekt dynamische Daten speichern und abfragen, muss man ein anderes Attribut, diesmal das 'resolve'-Attribut verwenden. Dieses Attribut hat auch ein Objekt als Wert, welches beliebige Attribute enthalten kann (wie im letzten Abschnitt zu statischen Daten). 
Der Unterschied zur Definition von statischen Daten ist, dass die Values der Attribute 'resolver'-Funktionen sind, die gleich erklärt werden.
```TypeScript
{  
  path: 'users/:userId',  
  component: UserTasksComponent,  
  children: userRoutes,  
  resolve: {  
    userName: resolveUserName  
  }  
}
```
Um Daten, die sich innerhalb eines 'resolve'-Objekts befinden, abzufragen, muss man eine 'resolver-function' verwenden. Diese Funktion befindet sich _ausserhalb!_ der Component-Klasse!!!!
```TypeScript
export const resolveUserName: ResolveFn<string> = (  
  activatedRoute: ActivatedRouteSnapshot,  
  routerState: RouterStateSnapshot  
) => {  
  const usersService = inject(UsersService);  
  return usersService.users.find(  
      (u) => u.id === activatedRoute.paramMap.get('userId')  
    )?.name || '';  
}
```
Diese 'resolver'-Funktion definiert den dynamischen Wert, der innerhalb der Routes-Konfig gespeichert wird.
Wenn man die Option 'withComponentInputBinding()' aktiviert hat, kann man diesen Wert nun als Input abfragen:
```TypeScript
userName = input.required<string>()
```
Im Hintergrund wird dann die oben definierte 'resolve'-Funktion getriggert, welche den Username ermittelt und zurückgibt.

> [!WARNING] 'resolver'-Funktionen werden nur dann neu ausgelöst, wenn sich eine Route-Variable ändert. Nicht, wenn sich ein Query-Parameter ändert!!!
> Wenn man das ändern will, sodass 'resolver'-Funktionen auch bei der Änderung von Query-Parametern neu ausgelöst werden, muss man dem Routing-Konfigurationsobjekt noch die folgende Zeile hinzufügen: ```runGuardsAndResolvers: 'paramsOrQueryParamsChange'```
## Abfragen von Daten in der Routing-Config ohne input()
Man kann statische und dynamische Daten in der Routing-Config auch abfragen, ohne 'input()' zu verwenden. Das ist zum Beispiel ein Muss, wenn man Angular <16 nutzt, da 'input()' erst ab Version 16 verfügbar ist!

Um diese Daten ohne 'input()' abzufragen, muss man ein 'activatedRoute'-Objekt verwenden und dieses in den Component injecten. 'activatedRoute' hat ein Attribut 'data', welches sowohl die statischen als auch die dynamischen Daten des Route-Konfigurationsobjekts enthält:
```TypeScript
@Component({ .. })  
export class UserTasksComponent implements OnInit {  
  //userName = input.required<string>()  
  //message = input.required<string>();  
  private activatedRoute = inject(ActivatedRoute)  
  
  ngOnInit() {  
    this.activatedRoute.data.subscribe({  
      next: (data) => {  
        console.log(data);  
      }  
    })  
  }  
}
```
Hier wird nun anstatt der beiden Input-Variablen eine Subscription zu 'activatedRoute.data' verwendet. Der Output des 'log'-Statements könnte wie folgt aussehen:
```TypeScript
Object { message: "Hello", userName: "Emily Thompson" }
```

# Routes rendern
Wenn man das obere Beispiel nimmt, um eine 'tasks'-Page zu implementieren, fehlt noch etwas, bevor man die Seite "/tasks" erreichen kann. Denn Angular weis nicht, wo es den "TasksComponent" rendern soll!

In der Datei "app-component.html" muss der Tag '<router-outlet/>' hinzugefügt werden. Dieser Header gibt an, wo der Component, der bei der Route definiert worden ist, eingefügt werden muss. Konkret wird der Component _nach_ dem '<router-outlet/>'-Tag eingefügt.
```HTML
<app-header />  
  
<main>  
  <app-users />  
  <div>    
	  <router-outlet/>  
  </div>
</main>
```
# Mehrere Routes definieren
Um mehrere Routes zu definieren, kann man dem Konfigurationsobjekt des Routers einfach mehr Objekte hinzufügen:
```TypeScript
export const routes: Routes = [  
  {  
    path: '',  
    component: NoTaskComponent,  
  },  
  {  
    path: 'tasks',  
    component: TasksComponent  
  },  
]
```
In diesem Fall wird bei der Route "/" nun der "NoTaskComponent" angezeigt.

## 'not found'-Route
Wenn man alle Routes, die nicht definiert sind, zu einer 'not-existing'-Page leiten möchte, kann man zur Liste der Routes das folgende Konfigurationsobjekt hinzufügen:
```TypeScript
{  
  path: '**',  
  component: NotFoundComponent  
}
```
Nun werden alle Routes, die nicht spezifiziert sind, zum 'NotFoundComponent' führen.
## Redirecting Routes
Möchte man eine bestimmte URL zu einer anderen URL weiterleiten, kann man das mit dem 'redirectTo'-Attribut machen. Man muss das folgende Objekt zur Liste der Route-Konfigurationsobjekte hinzufügen:
```TypeScript
{
	path: 'urlIwantToRedirectFrom',
	redirectTo: 'urlIwantToRedirectTo'
}
```
Wenn man mit [[#Nested Routes]] arbeitet, kann man als Path auch ```''```verwenden, um den Link des Parent-Elements umzuleiten.
# Routes mit Page-Titeln versehen
Es ist möglich, die verschiedenen Routes mit unterschiedlichen Titeln zu konfigurieren, sodass der Tab im Browser je nach Page einen anderen Text anzeigt.
Dafür muss man der Route-Konfiguration das Attribut 'title' hinzufügen:
```TypeScript
{  
  path: '',  
  component: NoTaskComponent,  
  title: 'No task selected',  
}
```
Nun wird bei dieser Route der Tab-Titel als 'No task selected' angezeigt.

Will man einen nicht-statischen Titel, kann man anstatt eines Strings auch eine Resolver-Funktion verwenden:
```TypeScript
export const resolveTitle: ResolveFn<string> = (  
  activatedRoute: ActivatedRouteSnapshot,  
  routerState: RouterStateSnapshot  
)=> {  
  return resolveUserName(activatedRoute, routerState) + "\'s Task"  
}
```
Diese Resolver-Funktion wird in der Datei des Components, aber _ausserhalb seiner Klasse_ definiert. Sie ruft eine andere Resolver-Funktion auf, die den Namen des aktuell geladenen Users zurückgibt und fügt diesen Namen zum Titel hinzu.

Die Resolver-Funktion kann nun mit dem Route-Konfigurationsobjekt mit dem 'title'-Attribut verbunden werden:
```TypeScript
{  
  path: 'tasks',  
  component: TasksComponent,  
  runGuardsAndResolvers: 'paramsOrQueryParamsChange',  
  title: resolveTitle,  
}
```
# Links erstellen
## routerLink
Mit einem ```<a href="..."></a>```-Tag zu arbeiten, um von einer Page zur anderen zu kommen, wird in Angular _nicht_ empfohlen.
Stattdessen sollte man routerLink verwenden:
```HTML
<a routerLink="/tasks"></a>
```
Der routerLink verhindert das normale Verhalten vom Browser und überlässt Angular das Routing zur anderen Page. So kann das Routen genau so abgewickelt werden, wie es von Angular vorgesehen ist.

> [!NOTE] Der im routerLink definierte Link ist immer relativ zur bestehenden Route!
> Wenn der Link '/tasks' im oberen Beispiel zB. innerhalb von [[#Nested Routes]] ist, wird er am Schluss der bestehenden Route angefügt!

## routerLinkActive
Angular hat eine eingebaute Methode, mit der man Elemente, die die aktuell geladenen Page verlinken, hervorheben kann.

Wenn man zB. Buttons für Home, About etc hat und will, dass der Home-Button auf der Home-Page leuchtet und der About-Button auf der About-Page, dann kann man das mit 'routerLinkActive' sehr leicht umsetzen.
```HTML
  <a routerLink="/home" routerLinkActive="active-link">Home</a>
```
'active-link' ist die CSS-Klasse, die dem Component hinzugefügt wird, wenn die geladene Route der Webseite der des HTML-Links des Components entspricht. Man kann diese CSS-Klasse auch mit einer eigenen Klasse ersetzen.
So wird immer nur ein Component auf dem Screen die 'active-link'-Klasse haben und aufleuchten.
## Programmatische Links
Um die Route mit Code ändern zu können, muss man den Router-Service in seinen Component injecten - 'private router = inject(Router)'.
Darauf kann man beim Router die 'navigate'-Funktion aufrufen, um den User zu einer bestimmten Route zu navigieren:
```TypeScript
@Component({ .. })  
export class NewTaskComponent {  
  userId = input.required<string>();
  private router = inject(Router)  
  
  onSubmit() {  
    this.router.navigate(['/users', this.userId(), 'tasks'], {  
      replaceUrl: true,  
    });  
  }  
}
```
'replaceUrl: true' bewirkt, dass Nutzer mit dem 'back'-Button des Browsers nicht zu der Seite des Components zurück kommen. Stattdessen werden sie zur davor geladenen Seite navigiert.
Das ist nützlich damit der User nicht zu einem Formular zurück kommt, das er soeben ausgefüllt hat.
# Dynamische Routes
Die meisten ausgereiften Webseiten wollen nicht nur statisch implementierte Routes ("/tasks", "/users") sondern auch dynamische Routes ("/users/1", "/tasks/8") implementieren.
## Dynamische Routes enablen
Um eine dynamische Route zu enablen muss man bei den Routing-Konfigurationsobjekten eine Route auf folgende Weise definieren:
```TypeScript
export const routes: Routes = [    
  {  
    path: 'users/:userId',  
    component: UserTasksComponent  
  },  
]
```
Die Variabel der dynamischen Route ist mit einem Doppelpunkt (":") gekennzeichnet. Man könnte anstatt 'users/:userId' auch einfach ':userId' verwenden - das spielt keine Rolle.
## Dynamische Routes verlinken
Wenn man nun eine dynamische Route verlinken will, muss man diese häufig auch dynamisch generieren. Im folgenden Beispiel hat der Component ein 'User'-Objekt gespeichert, welches eine Id enthält, die in der Route eingefügt wird:
```HTML
  <a [routerLink]="['/users', user().id]"></a>
```
Da der Wert von 'routerLink' hier dynamisch gesetzt wird, muss man [[Dynamische Daten#Property Binding]] verwenden. Das bedeutet, dass man den 'routerLink' in eckige Klammern setzt. 

Das Generieren des Wertes von 'routerLink' kann man mit Hilfe von Angular einfacher machen. Man könnte zwar [[Dynamische Daten#String Interpolation]] verwenden, doch Angular generiert URLs, wenn man die einzelnen Teile dafür als Array definiert. So wird aus ```['/users', user().id]```dann ```/users/123```. Den Schrägstrich zwischen den beiden Elementen generiert Angular von selbst.
## Parameter von dynamischen Routes abfragen
Wenn man nun dynamische Routes implementiert hat und zB. "/users/1" abfragen kann, möchte man diese dynamische Zahl meistens auch innerhalb von einem Component abfragen können. 

Um die Ziffer innerhalb der URL mit TypeScript abzufragen, muss man ein Input-Signal erstellen, welches den genau gleichen Namen hat, den der URL-Wert innerhalb des Routing-Konfigurationsobjekts hat!

Also wenn das Routing-Konfigurationsobjekt so aussieht:
```TypeScript
  {  
    path: 'users/:userId',  
    component: UserTasksComponent  
  }
```
Dann kann man die 'userId' auf folgende Weise innerhalb des Components abfragen:
```TypeScript
@Component({ .. })  
export class UserTasksComponent {  
  userId = input.required<string>()  
  private usersService = inject(UsersService);  
  
  userName = computed(()=>this.usersService.users.find(u=>u.id === this.userId()).name)  
}
```
In diesem Beispiel wird die userId dazu verwendet, im 'usersService' nach einer Person mit dieser Id zu suchen und ihren Namen zu speichern. 

> [!WARNING] Die userId ist keine Variable, sondern ein Signal!

Anstatt mit einem Signal zu arbeiten, kann man die dynamischen Werte auch mit folgender Zeile abfragen: 
```TypeScript
@Input({required: true}) userId!: string;
```
Mit dieser Zeile kann man die 'userId' genau so verwenden, wie im oberen Beispiel - nur ist sie dieses Mal kein Signal!

> [!WARNING] Um dynamische URL-Values mit 'Input' abzufragen, muss man in der 'bootstrapApplication'-Funktion den folgenden Code hinzufügen:

```TypeScript 
bootstrapApplication(AppComponent, {  
  providers: [  
    provideRouter(routes, withComponentInputBinding())  
  ]  
})
```
Die Methode 'withComponentInputBinding()' generiert ein Konfigurationsobjekt, welches das Abfragen von Werten in der URL mithilfe von 'input'-Methoden erlaubt.
## Parameter von dynamischen Routes mit Observables abfragen - activatedRoute
Mit 'input'-Funktionen die Parameter von dynamischen Routes abzufragen ist ein relativ neues Feature von Angular und ist bei weitem nicht in jedem Projekt so umgesetzt. 
Stattdessen lassen sich diese Werte auch mit einem [[Observable]] abfragen!
```TypeScript
@Component({ .. })  
export class UserTasksComponent implements OnInit {  
  private activatedRoute = inject(ActivatedRoute);  
  userId = '';
  
  ngOnInit(){  
    this.activatedRoute.paramMap.subscribe({  
      next: paramMap => {
	      this.userId = paramMap.get('userId')
      }  
    })  
  } 
}
```
Durch das Injecten von 'ActivatedRoute' bekommt man Zugriff auf ein Objekt, das die Route-Parameter enthält.

Es gibt eine Möglichkeit, ohne eine Subscription auf die Attribute von 'activatedRoute' zuzugreifen. Wenn man das 'snapshot'-Attribut der 'activatedRoute' verwendet, hat man Zugriff auf all deren Attribute als normale Variablen (anstelle von [[Observable]]s).
```TypeScript
@Component({ .. })  
export class UserTasksComponent implements OnInit {  
  private activatedRoute = inject(ActivatedRoute);  
  userId = '';

  ngOnInit(){  
    this.userId = this.activatedRoute.snapshot.paramMap.get('userId')
  } 
}
```

> [!WARNING] Ohne eine Subscription wird die Funktion nicht erneut ausgelöst, wenn sich der Wert des Parameters ändert!
> In diesem Beispiel würde die UserId den Wert behalten, den sie beim ersten Laden der Seite hatte!
> Aus diesem Grund sollte 'activatedRoute.snapshot' nur verwendet werden, wenn der Component nur ein Mal genutzt wird (nicht wie hier für alle User)!

# Nested Routes
Will man einer Route Kinder geben, muss man das auf folgende Weise machen; in der Konfigurationsdatei, wo die Routes definiert werden, kann man der gewünschten Route das Attribut 'children' geben:
```TypeScript 
export const routes: Routes = [  
  {  
    path: '',  
    component: NoTaskComponent,  
  },  
  {  
    path: 'users/:userId',  
    component: UserTasksComponent,
    children: [
    
    ]
  },  
]
```
In diesem Beispiel wird die Route 'users/' mit Children erweitert. 
```TypeScript
export const routes: Routes = [  
  {  
    path: '',  
    component: NoTaskComponent,  
  },  
  {  
    path: 'users/:userId',  
    component: UserTasksComponent,  
    children: [  
      {  
        path: 'tasks',  
        component: TasksComponent,  
      }  
    ]  
  },  
]
```
Nun wurde in das Array der Children ein Child hinzugefügt. Dieses Konfigurationsobjekt ist genau gleich aufgebaut wie das der anderen Pfade - es enthält den Pfad, mit dem man darauf zugreifen kann und den Component, den dieser Pfad laden soll.

Bei einem Child-Path wird dessen Pfad an den des Parents angehängt. In diesem Beispiel ist der Pfad zu 'tasks' also:
```
domain-name/users/<userId>/task
```
## Nested Routes rendern
Wenn man einen Child-Path definiert hat, muss man noch festlegen, wo dessen Component gerendert werden soll. Bei normalen Routes macht man das mit 'router-outlet'.

> [!NOTE] Child-Routes brauchen ein eigenes 'router-outlet' in dem Component, dessen Child sie sind!

Im Beispiel von [[#Nested Routes]] muss man für die Child-Route 'tasks' das 'router-outlet' im Parent-Component 'UserTasksComponent' definieren (siehe [[#Routes rendern]]).
## Parameter von Parent-Routes abfragen
Wenn man zur Route ```/users/<userId>``` die Child-Route ```tasks```hinzufügt und innerhalb von der Child-Route die UserId verarbeiten will (zB. um die Tasks des Users anzuzeigen), muss man zunächst app.config.ts / main.ts konfigurieren.

Im Abschnitt [[#Parameter von dynamischen Routes abfragen]] musste innerhalb von 'main.ts' bzw 'app.config.ts' (je nach Projekt unterschiedlich) die Abfrage von Parametern mit '@Input' in der Funktion 'provideRouter()' ermöglicht werden.

Um auf die Parameter von Parent-Routes zuzugreifen, muss man nun ebenfalls ein Argument zur Methode 'provideRouters()' hinzufügen. Dieses Argument ist die Funktion 'withRouterConfig()', welche ein Konfigurationsobjekt enthält:
```TypeScript
bootstrapApplication(AppComponent, {  
	providers: [  
		provideRouter(routes, withComponentInputBinding(), withRouterConfig({  
			paramsInheritanceStrategy: 'always'  
		}))  
	]  
}).catch((err) => console.error(err));
```
Die 'paramsInheritanceStrategy' sorgt dafür, dass die Route-Parameter der Parents immer in die Routes der Kinder übertragen werden.

Nun können Route-Parameter so wie im Abschnitt [[#Parameter von dynamischen Routes abfragen]] abgefragt werden.
# Query-Parameter
## Setzen von Parametern
Um zB. einen Parameter für die Sortierreihenfolge hinzuzufügen - '?order=asc' - definiert man diese in einem Link.
```HTML
<a routerLink="./" [queryParams]="{order: 'asc'}">  
  Sort Asc / Desc  
</a>
```
- ```routerLink``` verweist auf den bestehenden Pfad - man bleibt also auf der Seite, auf der man bereits ist.
- ```[queryParams]```definiert die Parameter in einem Objekt. In diesem Fall wird die Route so aussehen: ```meinPfad/?order=asc```
## Auslesen von Parametern
Wenn man in der Konfiguration des Routers (siehe [[#Routing in Angular konfigurieren]]) 'withComponentInputBinding' aktiviert hat, kann man ganz einfach mit 'input<>()' auf die Parameter zugreifen. 
Hat man also den Parameter 'order' so wie im oberen Beispiel definiert, kann man diesen in einem Component mit der folgenden Zeile abfragen:
```TypeScript
order = input<'asc'|'desc'>();
```
## Auslesen von Parametern mit Observables
So wie beim Abfragen von Dynamischen Route-Values kann man Parameter in der URL ebenfalls mit einem [[Observable]] abfragen.

So wie im Kapitel [[#Parameter von dynamischen Routes mit Observables abfragen - activatedRoute]], nutzt man auch hier das 'activatedRoute'-Objekt, welches in den Component injected werden muss.
```TypeScript
private activatedRoute = inject(ActivatedRoute)
```
Dieses Mal nutzt man das 'queryParams'-Attribut und subscribed zu diesem. Dies sollte man innerhalb von 'ngOnInit' machen. In der gleichen Funktion muss man unbedingt die Funktion 'destroyRef.onDestroy()' mit einem 'unsubscribe()' verbinden - so wie im folgenden Beispiel:
```TypeScript
ngOnInit(){  
  const subscription = this.activatedRoute.queryParams.subscribe({  
    next: params => this.order = params['order'],  
  })  
  
  this.destroyRef.onDestroy(()=> subscription.unsubscribe())  
}
```
Nun ist die Variable 'order' mit dem URL-Parameter namens 'order' verbunden. Wegen der Subscription ändert sich die Variable, wenn sich der Parameter ändert.
# Route Guards
Rout Guards sind Funktionen, die Prüfen, ob eine bestimmte Navigation-Actions erlaubt sind. Praktisch kontrollieren sie den Zugriff auf eine Route.
## canMatch
Die Logik, welche über den Zugriff auf eine Route bestimmt, ist in einer Resolver-Funktion gespeichert. Diese Resolver-Funktion kann irgendwo in der Applikation gespeichert sein, beispielsweise direkt innerhalb der Routing-Konfiguration.

Innerhalb des Route-Konfigurationsobjekts wird diese Funktion (in diesem Fall 'dummyCanMatch') als Value des 'canMatch'-Attributs gesetzt:
```TypeScript
{  
  path: 'users/:userId',  
  component: UserTasksComponent,  
  children: userRoutes,  
  canMatch: [dummyCanMatch],  
}
```
Die Funktion 'dummyCanMatch' _muss_ eine Boolean zurückgeben, je nach dem, ob auf die Route zugegriffen werden kann, oder nicht:
```TypeScript
const dummyCanMatch: CanMatchFn = (route, segments) => {  
  const router = inject(Router)  
  const shouldAccess = Math.random()  
  if (shouldAccess < 0.5){  
    return true;  
  }else{  
    return new RedirectCommand(router.parseUrl('/unauthorized'))  
  }  
}
```
In diesem Fall wird anhand von einer zufälligen Zahl bestummen, ob der Access erlaubt wird (true), oder ob ein Redirect getriggert wird (RedirectCommand).
## canDeactivate
Mit 'canDeactivate' kann man bestimmen, ob ein User eine Page verlassen darf.
```TypeScript
export const canLeaveEditPage: CanDeactivateFn<NewTaskComponent> = (component) => {  
  if(component.enteredTitle() || component.enteredSummary() || component.enteredDate()){  
    return window.confirm("Do you really want to leave? You will use the entered Data!")  
  }else{  
    return true;  
  }  
}
```
Diese Funktion, welche zu einem Formular-Component gehört, prüft, ob das Formular bestehende Daten hat und fragt den User in diesem Fall, ob er die Seite wirklich verlassen will.
Auf die Daten des Formulars kann er zugreifen weil der Component, der momentan geladen ist, der Funktion als Argument mitgegeben wird!

Nun muss die Funktion nur noch dem Router-Konfigurationsobjekt hinzugefügt werden. Wie bei 'canMatch' auch hier innerhalb eines Arrays:
```TypeScript
{  
  path: 'tasks/new',  
  component: NewTaskComponent,  
  canDeactivate: [canLeaveEditPage]  
}
```
# Pages reloaden
Manchmal will man eine Seite programmatisch neu laden - zum Beispiel um bestimmte Daten zu aktualisieren.

Wenn man beispielsweise eine Liste von Einträgen hat und einen davon löschen will, dann sollte die Seite neu laden, sodass eine neue Liste ohne den soeben gelöschten Eintrag dargestellt werden kann.

Es wäre zu einfach, wenn man die Seite einfach neu laden könnte - stattdessen muss man den folgenden Code verwenden:
```TypeScript
@Component({ .. })  
export class TaskComponent {  
  task = input.required<Task>();  
  private tasksService = inject(TasksService);  
  private router = inject(Router);  
  private activatedRoute = inject(ActivatedRoute);  
  
  onComplete() {  
    this.tasksService.removeTask(this.task().id);  
    this.router.navigate(['./'], {  
      relativeTo: this.activatedRoute,  
      onSameUrlNavigation: "reload",  
      queryParamsHandling: 'preserve'  
    });  
  }  
}
```
Die Funktion 'onComplete()' löscht einen Task aus der Liste aller Tasks, die im TaskService gespeichert ist. 
Danach wird die Funktion 'navigate' des Routers getriggert.
- relativeTo -> der angegebene Pfad ist relativ zum aktuell geladenen
- onSameUrlNavigation -> Die Seite soll neu geladen werden, als ob man von einer anderen Page aus darauf landen würde
- queryParamsHandeling -> Die Queryparameter sollen erhalten bleiben. Wird diese Option nicht verwendet, werden die Parameter gelöscht.

Zusätzlich muss im Route-Konfigurationsobjekt die Zeile ```runGuardsAndResolvers: 'always'``` hinzugefügt werden:
```TypeScript
{  
  path: 'tasks', // <your-domain>/users/<uid>/tasks  
  component: TasksComponent,  
  runGuardsAndResolvers: 'always',  
  title: resolveTitle,  
  resolve: {  
    userTasks: resolveUserTasks,  
  },  
}
```