#angular 
#JavaScript 
#frontend 
Ein Service ist eine Klasse, die mehrmals benutzt werden kann und eine spezifische Aufgabe erledigt. Services können in Components injected werden.

Services werden dazu benutzt, business-Logik, Datenzugriff und utility-Funktionen von UI-Komponenten zu trennen.
# Service erstellen
Die Datei, in der ein Service geschrieben wird, ist auf folgende Weise benannt:
'NAME.service.ts'.
Innerhalb von diesem Service erstellt man eine Klasse, die die Logik vom Service enthält:
```TypeScript
@Injectable({  
  providedIn: 'root'  
})
export class TaskService {
	tasks = [...]

	addTask(){...}

	removeTask(){...}
}
```
Achtung -> Anstatt '@Component' wird hier '@Injectable' verwendet!
# Service nutzen
Um einen Service korrekt zu nutzen, reicht es nicht aus, diesen in einer anderen Klasse zu initialisieren. Angular will, dass man den Service im Konstruktor von anderen Klassen mit _Dependency Injection_ erstellt!
```TypeScript
export class TaskComponent{
	constructor(private taskService: TaskService){}
}
```
In diesem Beispiel wurde ein Konstruktor erstellt, in dem ein TaskService erwartet wird. Angular erstellt diesen dann für uns. "Wir sagen, welchen Datentyp wir von Angular wollen. Angular erstellt dann für uns eine Instanz, die es uns weitergibt".

Dadurch, dass der 'taskService' bereits mit 'private' ausgestattet ist, muss man die Variabel nicht selber erstellen, sondern kann diese direkt nutzen!

> [!NOTE] Angular gibt immer dasselbe Service-Objekt aus und eignet sich somit für globalen State!

Alternativ kann man den Service auch auf folgende Weise in einen Component einbinden:
```TypeScript
export class TaskComponent{
	private taskService = inject(TasksService)
}
```