#JavaScript 
#angular 
#frontend 
Es gibt verschiedene Arten, wie man seine TS-Werte vom [[Component]] ins HTML einbinden kann.
## String Interpolation
String Interpolation ist eine wichtige Funktion von React. Sie erlaubt, im TS definierte Werte innerhalb vom HTML eines Components darzustellen. 
```TypeScript
@Component({ ... })
export class AppComponent {
	myValue = "Hallo Welt"
}
```
In diesem Component wurde innerhalb der Klasse eine Variable mit dem Wert "Hallo Welt" definiert. Nun wird sie im HTML des Components eingebunden:
```HTML
<header>  
  <img src="assets/angular-logo.png" alt="The Angular logo: The letter 'A'" />  
  <h1>Let's get started!</h1>  
  <p>Time to learn all about Angulaaaarus!</p> 
  <p>{{ myValue }}</p> 
</header>
```

> [!WARNING] Achtung
> String Interpolation wird nur für Content zwischen Tags verwendet. Um Properties von Tags (wie die Src eines Bildes) zu definieren, muss man [[#Property Binding]] verwenden.

Anstatt einer einzelnen Variable kann man innerhalb der doppelten Klammer auch andere TS-Ausdrücke verwenden:
```HTML
<p>{{ myValue / 3 }}<p/>
```
Dieser Ausdruck ist beispielsweise ebenfalls gültig. Man sollte aber so viele Berechnungen wie möglich ausserhalb vom HTML machen!!!
## Property Binding
Anstatt eine Property mit einem eingebunden String zu definierten, muss man diese auf folgende Weise einbinden:
```HTML
<div>  
  <button>    
	  <img [src]="'assets/users/' + selectedUser.avatar"/>  
  </button>
</div>
```
- Der Name der gesetzten Property muss mit eckigen Klammern umrandet sein.
- In diesem Fall wird zur Variabel "selectedUser.avatar" noch ein Pfad angegeben, der fester Teil der Property ist.

> [!WARNING] Achtung
> Die Berechnung des Pfades in diesem Beispiel sollte innerhalb der Typescript-Datei des Components berechnet und erst dann importiert werden. Hierzu könnte man einen [[#Getter für berechnete Werte]] verwenden.
## Getter für berechnete Werte
Anstatt einen Wert innerhalb vom HTML zu berechnen, kann man im TypeScript einen Getter definieren, der innerhalb vom HTML aufgerufen wird:
```TypeScript
import { Component } from '@angular/core';

@Component({
	selector: 'app-root',
	standalone: true,
	imports: [],
	templateUrl: './app.component.html',
	styleUrl: './app.component.css',
})
export class AppComponent {
	myValue = "Hallo Welt"

	get imagePath(){
		return 'assets/users/' + this.myValue;
	}
}
```
```HTML
<img [src]="imagePath"/>
```
Durch das Aufrufen von 'imagePath' wird der entsprechende Getter im TypeScript aufgerufen. Obwohl 'imagePath' eine Funktion ist, wird sie im HTML wie eine Variabel verwendet.

> [!WARNING] Signale verwenden keine Getter, sondern Computed-Values!


