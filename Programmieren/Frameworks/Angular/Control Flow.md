#angular 
#JavaScript 
#frontend 
Der Control Flow von einem [[Component]]wird auch innerhalb des HTML-Elements definiert. 
# Listen rendern
Um den Inhalt einer Liste dynamisch zu rendern, kann man auf folgende Weise einen for-Loop nutzen:
```HTML
<ul id="users">  
	@for(user of users; track user.id){  
	  <li>  
		<app-user [user]="user"  
				  (select)="onSelectUser($event)"/>  
	  </li>    
	}  
</ul>  
```
Mit diesem Loop wird über das 'users'-Array geloopt und jeder User als Attribut von einem 'app-user'-[[Component]] verarbeitet.

Mit 'track user.id' definiert man den einzigartigen Identifier, der die Elemente der Liste unterscheidet.
## Leere Listen - Fallback
Mit der '@empty'-Annotation kann man ein Fallback erstellen, welches bei einer leeren Liste verwendet wird:
```HTML
<ul>  
  @for (ticket of tickets; track ticket.id){  
    <li>  
      <app-ticket />    
    </li>  
  } @empty {  
    <p>No tickets available</p>  
  }  
</ul>
```
## Weitere '@for'-Funktionalitäten
### First / Last
Für das erste und letzte Element des Arrays, über das man loopt, gibt es je eine Boolean, welche je ein Mal 'true' ist:
```HTML
<ul>  
  @for (ticket of tickets; track ticket.id){  
    <li>  
      <app-ticket /> - {{$last}}  
    </li>  
  } @empty {  
    <p>No tickets available</p>  
  }  
</ul>
```
Dieser Code wird beim letzen Element das Wort 'true' rendern. 
### Even / Odd
Mit $even und $odd kann man abfragen, ob das aktuelle Listenelement einen geraden oder ungeraden Index hat.
### Count
Mit '$count' bekommt man die Anzahl aller Elemente in der Liste.
# Konditionales Rendern
Will man ein bestimmtes Element nur unter bestimmten Bedingungen rendern, muss man das folgende 'if'-statement verwenden:
```HTML
@if (userName()){
	<app-tasks [userName]="userName()!"
}
```
Dieser Codeabschnitt fragt, ob 'userName' definiert ist. Ist der UserName nicht null, wird das 'app-tasks'-Element gerendert.

Zusätzlich könnte man noch ein Fallback machen, das angezeigt wird, wenn der userName undefined ist:
```HTML
@if (selectedUserName()){  
  <app-tasks [userName]="selectedUserName()!"/>  
} @else {  
  <p id="fallback">Select a user to see their tasks</p> 
}
```
# Alternativer Syntax
Anstatt '@for' und '@if' zu verwenden, kann man auch mit '*ngFor' und 'ngIf' arbeiten.
## For
```HTML
<ul id="users">  
  <li *ngFor="let user of users">  
	<app-user [user]="user"  
			  (select)="onSelectUser($event)"/>  
  </li>    
</ul>  
```
## If
```HTML

<app-tasks *ngIf="selectedUser; else fallback" [userName]="selectedUserName()!"/>  
<ng-template #fallback>
  <p id="fallback">Select a user to see their tasks</p> 
</ng-template>
```