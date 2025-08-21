#JavaScript 
#frontend 
#angular 
Mit ngModel kann man Daten zwischen einem Eingabefeld und einer entsprechenden Variabel synchronisieren. Wird eines der beiden verändert, werden beide verändert! Diese Art von Verbindung wird Two-Way-Binding genannt.

Zunächst muss man innerhalb des [[Component]] eine Variabel definieren:
```TypeScript
export class NewTaskComponent {  
	enteredTitle = '';   
}
```
Dann kann man diesen Wert mit einem Eingabefeld verbinden:
```HTML
<input type="text" id="title" name="title" [(ngModel)]="enteredTitle"/>
```
# onSubmit
Man kann die Submission eines Formulars durch das Attribut 'ngSubmit' mit einer Funktion (hier 'onSubmit()') verbinden. 
```HTML
<form (ngSubmit)="onSubmit()">
	...
</form>
```
# Komplexere Formulare
Mit [[Template Values]] lassen sich auch komplexe Formulare sehr einfach verarbeiten.
# Two Way binding über Components hinweg
Was ist, wenn ein Component von seinem Parent einen Input erhält, der bei einer Änderung auch beim Parent geändert werden soll? Zb. wenn ein Component einen Nutzernamen verarbeiten soll, der eigentlich im Parent gespeichert ist. Wenn das Kind den Wert ändert, muss diese Änderung auch im Parent-Component vorgenommen werden.
```TypeScript
@Component({ ... })
export class ChildComponent {
	@Input() username!: string;

	onNameChange(newValue: string){
	
	}
}
```
Hier muss noch ein Output hinzugefügt werden, der bei der Änderung des Namens getriggert wird. Wenn man den Output nach dem Schema 'name+"Change"' benennt, kann man mit Angular automatisch die Value des Parents updaten:
```TypeScript
@Component({ ... })
export class ChildComponent {
	@Input() username!: string;
	@Output() usernameChange = new EventEmitter<string>();

	onNameChange(newValue: string){
		this.usernameChange.emit(newValue);
	}
}
```
Nun kann im Html des Parents folgendes stehen:
```HTML
<app-child [(username)]="username"/>
```
Somit ist der Username zugleich der Wert, welcher als Input weitergegeben wird und auch der Wert, welcher beim Empfangen des Outputs neu gesetzt wird. 
## Two Way Binding mit model() - weniger Aufwand
Es gibt einen Weg mit dem man Two Way Binding erreichen kann, ohne Inputs und Outputs zu verwenden.
Dafür muss man den Code vom oberen Beispiel kaum verändern - anstelle von Input und Output schreibt man folgende Zeile:
```TypeScript
size = model.required<{ width: string, height: string }>()
```
Wenn man 'size' als 'model' definiert (was Teil der [[Signale]] ist), übernimmt Angular die In- und Outputs