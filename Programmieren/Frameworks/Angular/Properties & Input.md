#JavaScript 
#angular 
#frontend 

Will man einen Component mit eigenen Properties ausstatten, zB:
```HTML
<app-user [avatar]="users[0].avatar"  
[name]="users[0].name"/>
```
...dann kann man das mit oder ohne Signale machen. Wichtig ist, dass sich die Nutzung der Properties nicht durch ihre Definition verändert!
# ...ohne Signale
```TypeScript 
@Component({  
    selector: 'app-user',  
    standalone: true,  
    imports: [],  
    templateUrl: './user.component.html',  
    styleUrl: './user.component.css'  
})  
export class UserComponent {  
     @Input() avatar!: string;  
     @Input() name!: string;  
}
```
Mit '@input' wird die Variable, welche als Attribut verwendet wird, definiert. 

Wie bei der Konfiguration eines Components kann man auch das '@Input'-Attribut mit einem Konfigurationsobjekt konfigurieren:
```TypeScript
@Input({ required: false }) avatar!: string;
```
In diesem Fall wird beispielsweise festgelegt, dass der String 'avatar' nicht unbedingt gesetzt werden muss. Um bei vergessenen Properties einen Error zu generieren, muss diese Konfiguration auf True gesetzt werden.

## Objekte empfangen
Was ist, wenn man einen komplexen Datentyp anstatt eines einfachen Strings empfangen will?
```TypeScript
@Component({  
    selector: 'app-user',  
    standalone: true,  
    imports: [],  
    templateUrl: './user.component.html',  
    styleUrl: './user.component.css'  
})  
export class UserComponent {  
     @Input() user!: {
	     name: string,
	     avatar: string
     }; 
}
```
# ...mit Signalen
```TypeScript
avatar = input<string>()  
name = input<string>("Basti")
```
- Mit dem Datentyp innerhalb der spitzen Klammer wird definiert, was für einen Datentyp Angular für diese Variabel erwarten soll.
- Der String innerhalb der runden Klammer definiert den Standartwert des Attributs.

Will man, dass das Attribut unbedingt gesetzt werden muss, kann man '.required' vor die runde Klammer setzen:
```TypeScript
avatar = input.required<string>()  
name = input.required<string>()
```
Hier kann kein Standartwert gesetzt werden, da der Wert unbedingt gesetzt werden muss.

Diese Signal-Inputs sind Signale und müssen als solche genutzt werden (mit runden Klammern abfragen -> 'avatar()'). 

Diese Signal-Inputs sind read only!
# Änderungen von Properties verarbeiten
Um Änderungen von Properties zu verarbeiten, muss man die 'ngOnChanges'-Methode verwenden, die in [[Component Lifecycle#ngOnChanges]] genauer erklärt wird.
# Input-Konfiguration
So wie Components können auch Inputs ein Konfigurationsobject erhalten, welches deren Eigenschaften festhält.
Es gibt für Inputs drei wichtige Konfigurationsdaten, welche man wissen muss:
## Required
Mit '{required: true}' zwingt man die Applikation dazu, dass ein Wert für den Input vorhanden sein muss! Wenn man das nicht macht, muss man bei der Definition des Types alternativ auch noch 'undefinded' angeben.
## Alias
```TypeScript
data = input.required<Ticket>({alias: 'ticket'});
```
Mit dem Alias kann man dem Input einen anderen Namen geben, unter dem er dann im HTML ansprechbar ist. Alias sollte nur verwendet werden, wenn man einen guten Grund dafür hat. Ansonsten ist Alias nicht notwendig.
Alias kann auch bei [[Events, Output]] verwendet werden!
## Transform
```TypeScript
data = input.required<Ticket>({transform: (value) => {}});
```
Mit Transform kann man den Wert des Inputs verarbeiten, wenn er gesetzt oder verändert wird. So kann man zB. die Daten bereinigen, bevor sie weiterverarbeitet werden.
Man muss aber aufpassen, dass die Nutzung von Transform nicht zu mehr unnötiger Komplexität und Verwirrung führt!
