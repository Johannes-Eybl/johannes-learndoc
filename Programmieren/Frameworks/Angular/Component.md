#angular 
#JavaScript 
#frontend 

Ein Angular-Component hat viele Ähnlichkeiten mit einem React-Component. Unterscheiden tuen sich die beiden in ihrer Definition (Angular mit Klassen, die dekoriert sind) und in der Weise, wie State gemanaged wird.
# Component erstellen
Ein Angular-Component besteht aus (in der Regel) 3 Dateien: Dem HTML, CSS und die TypeScript-Datei, die den Component definiert.

Benannt werden Components nach dem Schema: ```NAME.component.ts```. Da man in Angular auch andere Elemente neben Components erstellen kann, muss die neu erstellte Datei mit dem Namen "component" gekennzeichnet sein.
## app.component.ts
```TypeScript
import { Component } from '@angular/core';

@Component({
	selector: 'app-root',
	standalone: true,
	imports: [],
	templateUrl: './app.component.html',
	styleUrl: './app.component.css',
})
export class AppComponent {}
```

| Wert        | Erklärung                                                                                                                                                                              | Konvention                                           |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| selector    | Sagt Angular, nach welchen Elementen es im HTML suchen soll, damit diese Elemente dann durch den Component ersetzt werden. In diesem Fall ist das Element ```<app-root></app-root>```. | Wird normalerweise mit min. zwei Wörtern defininert. |
| standalone  | Definiert die Art von Component, der erstellt wird.                                                                                                                                    | true                                                 |
| imports     | In dieser Liste werden alle Components, die innerhalb von diesem Component genutzt werden, eingefügt.                                                                                  |                                                      |
| templateUrl | Wo das Html des Components gespeichert ist.                                                                                                                                            |                                                      |
| styleUrl    | Wo das CSS des Components gespeichert ist.                                                                                                                                             |                                                      |
## app.component.html
```HTML
<header>  
  <img src="assets/angular-logo.png" alt="The Angular logo: The letter 'A'" />  
  <h1>Let's get started!</h1>  
  <p>Time to learn all about Angulaaaarus!</p>  
</header>
```
## app.component.css
```CSS
header {  
  margin: 3rem auto;  
  text-align: center;  
}  
  
img {  
  width: 8rem;  
}  
  
h1 {  
  margin: 1rem auto;  
  background: -webkit-linear-gradient(45deg, #f9096d, #b700ff);  
  -webkit-background-clip: text;  
  -webkit-text-fill-color: transparent;  
  font-size: 3rem;  
}
```
# Component einbinden
Um den oben beschriebenen App-Container zu verwenden, muss man den Namen des Selectors in der Datei index.html einbinden.
```HTML
<body>
	<app-root></app-root>
</body>
```
Zudem muss man den neuen Component auch noch in der Datei 'main.ts' hinzufügen. Wenn man das nicht macht, erkennt Angular den neuen Component nicht und dieser wird nicht angezeigt.
```TypeScript
import { bootstrapApplication } from '@angular/platform-browser';  
  
import { AppComponent } from './app/app.component';    
  
bootstrapApplication(AppComponent).catch((err) => console.error(err));  
```
> [!WARNING] Achtung
> Normalerweise fügt man nicht jeden Component zu 'main.ts' hinzu. Stattdessen werden Components häufig in andere Components eingefügt.
# Generieren von Components mit der [[Angular-CLI]]
Man kann auch mit der [[Angular-CLI]] Components erstellen. 
```Bash
ng generate component NAME
```
oder 
```Bash
ng g c NAME
```
Diese zwei Befehle erstellen beide einen neuen Component mit dem Namen NAME. Dazu wird ein neuen NAME-Ordner generiert, in dem die drei Dateien des Components gespeichert sind.
# Wrapping Components
Wenn man beispielsweise eine eigene Card oder ein Modal erstellen möchte, das von verschiedenen Components gefüllt wird, muss man den Tag '<ng-content/>' als Platzhalter für diese Components verwenden:
```HTML
<div>
	<ng-content/>
</div>
```
'<ng-content/>' wird beim Kompilieren mit dem Content der eingebundenen Divs ersetzt.

Man kann auch beschränken, welche Elemente ein Component wrappen kann:
```HTML
<div class="control">
	<ng-content select="input, textarea"/>
</div>
```
Hier wird der mögliche Content auf zwei mögliche HTML-Tags beschränkt.
# CSS auf gewrappte Components
Im oberen Beispiel wurde ein Div mit der Klasse "control" definiert, welches einen Input oder eine Textarea einbindet.

Doch hier würde das folgende CSS nicht funktionieren:
```CSS
.control input,  
.control textarea {  
  width: 100%;  
  padding: 0.5rem;  
  border: 1px solid #ccc;  
  border-radius: 4px;  
  font: inherit;  
  font-size: 0.9rem;  
  color: #4f4b53;  
}
```
Angular sieht im HTML nur 'ng-content', also weder Input noch Textarea. Das liegt daran, dass Input und Textarea projiziert werden und somit ausserhalb der View vom Component liegen.
Damit die eingebundenen Tags richtig angezeigt werden, muss man im Konfigurationsobjekt von 'control.component.ts' folgende Zeile hinzufügen:
```TypeScript
{
...
encapsulation: ViewEncapsulation.None
...
}
```
Hier das gesamte Objekt:
```TypeScript
@Component({  
  selector: 'app-control',  
  standalone: true,  
  imports: [],  
  templateUrl: './control.component.html',  
  styleUrl: './control.component.css',  
  encapsulation: ViewEncapsulation.None  
})  
export class ControlComponent {  
}
```
Mit dieser Konfiguration wird das CSS nicht mehr auf diesen Component beschränkt, sondern wird global angewendet. Es wird nicht mehr auf den einen Component beschränkt (encapsulated), sondern global angewendet.
# Host-Element/Selector stylen
Manchmal will man innerhalb eines Components das Host-Element stylen. Also der Tag, unter dem der Component im HTML verwendet wird (zb. '<app-button/>'). Dieses CSS wird mit dem ':host'-Tag beschrieben:
```CSS
:host {  
  display: inline-block;  
  padding: 0.65rem 1.35rem;  
  border-radius: 0.25rem;  
  font-size: 1rem;  
  text-align: center;  
  cursor: pointer;  
  background-color: #691ebe;  
  color: white;  
  border: none;  
}  
  
:host:hover {  
  background-color: #551b98;  
}
```
In diesem Beispiel ist der Host in jedem Fall ein Button, dessen Hover-Effekt direkt innerhalb des Components gestyled wird.

> [!WARNING] ':host' kann nicht verwendet werden, wenn encapsulation: ViewEncapsulation.None ist!

# Attribute des Host-Elements setzen
Manchmal will man Attribute des Host-Elements setzten, beispielsweise die Klasse.
Dazu fügt man im Konfigurationsobjekt des Components folgendes Element hinzu:
```TypeScript
host: {  

}
```
Alle Key-Value-Paare, die innerhalb von diesem Objekt sitzen, werden dem Host-Element als Attribute hinzugefügt. Um eine Klasse zu definieren, schreibt man also:
```TypeScript
host: {  
  class: 'control',  
}
```
Man kann natürlich auch die Id und andere Werte setzen.

Alternativ kann man die Attribute des Host-Elements auch innerhalb von der Component-Klasse definieren:
```TypeScript
@Component({ ... })  
export class ControlComponent {  
  @HostBinding('class') class = "control";  
}
```
Innerhalb der '@HostBinding'-Annotation kann man jegliches Attribut des Hosts definieren.

> [!Warning] @HostBinding sollte nicht mehr verwendet werden. 
> Es existiert nur noch für backwards-compatability

# Auf Events des Host-Elements reagieren
Innerhalb des Host-Objekts im Konfigurationsobjekt eines Components kann man auch Funktionen mit Events verknüpfen:
```TypeScript
@Component({
  host: {  
  "(click)": "onklick()"  
  }  
})  
export class ControlComponent {
  onklick() {  
    console.log('onklick');  
  };  
}
```
Das gleiche Ergebnis kann auch auf folgende Weise erstellt werden:
```TypeScript
@Component({ ... })  
export class ControlComponent {
  @HostListener('click') onClick(): void {  
    console.log('click');  
  }  
}
```
