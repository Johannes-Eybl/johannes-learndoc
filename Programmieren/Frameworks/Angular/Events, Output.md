#JavaScript 
#angular 
#frontend 
In Angular werden Elemente mit EventListeners ausgestattet. Ein EventListener wird ganz einfach definiert:
```HTML
<button (click)="onUserClick()">MyBtn</button>
```
Entsprechend muss in der TypeScript-Klasse vom [[Component]] eine Funktion definiert sein:
```TypeScript
import { Component } from '@angular/core';  
  
@Component({  
  selector: 'app-user',  
  standalone: true,  
  imports: [],  
  templateUrl: './user.component.html',  
  styleUrl: './user.component.css'  
})  
export class UserComponent {  
  onSelectUser(){  
    console.log("Clicked!!!")  
  }  
}
```
# Custom Events
## Senden
Um ein neues Event zu definieren, muss man folgenden Code in den Component schreiben:
```TypeScript
// Erste Methode, alt
@Output() select = new EventEmitter<string>()
// Zweite Methode, neu
select = output<string>()
```
Anstatt 'string' könnte man hier auch andere Datentypen bzw. 'void' einfügen.
Um dieses Event auszulösen (innerhalb vom gleichen Component):
```TypeScript
this.select.emit("SomeID")
```
## Empfangen
Wenn man dieses Event in einem anderen Component empfangen und nutzen möchte, kann man das wie ein normales DOM-Event programmieren:
```HTML
<app-user (select)="onSelect($event)"/>
```
```TypeScript
onSelect(id: String) {  
  console.log(id)  
}
```
# Komplexer Umgang mit Events
Möchte man, dass eine Event-Variable zugleich auch der Input für ein Child ist, muss man sich im Kapitel [[Two Way Binding und Formulare]] über Two-Way-Binding informieren!