#JavaScript 
#angular 
#frontend 
Es gibt zwei Möglichkeiten, State mit Angular zu implementieren. Einerseits kann man mit Zone.js in HTML eingebettete Variablen direkt im TypeScript bearbeiten und Angular übernimmt das Updaten der Benutzeroberfläche.
Andererseits gibt es Signale, 
# Warum Signale?
Signale sind neuer als Zones und sollten wenn möglich verwendet werden. Der Vorteil von Signalen ist, dass sie effizienter sind und zukünftig vielleicht nicht mehr supportet werden.
# Zone.js
Wenn man in Angular [[Dynamische Daten]] verwendet, also Variablen direkt in das HTML einbindet, werden diese Teil des States - die Oberfläche ändert sich, wenn sich die Variablen ändern.
## Zone.js unter der Oberfläche
Angular findet automatisch heraus, wenn sich eine Variabel von einem [[Component]] ändert. Ist das der Fall, prüft Angular, ob das HTML vom [[Component]] anders dargestellt (=neu gerendert) werden muss.

Dieses automatische Updaten von State und Oberfläche ist ein Teil von Zone.js, ein Package aus dem Angular-Framework. Es verfolgt Operationen wie Timeouts, Requests oder User Input und meldet diese Events bei Angular, damit dieses die Oberfläche updaten kann.
# Signale
Ein Signal ist ein Objekt, das einen Wert speichert. Wird der Wert von diesem Objekt geändert, kann Angular den entsprechenden Teil vom UI updaten. 
Angular hat quasi eine Subscription zu jedem Signal und wird über Veränderungen informiert. Durch die Definition und das Abfragen von Signalen kann Angular die Werte von diesen Tracken und das UI ändern.
## Signal definieren, abfragen und verändern
Ein Signal wird innerhalb von der [[Component]]-Klasse auf folgende Weise definiert:
```TypeScript
export Class UserComponent {
	selectedUser = signal("Max Mustardman")
}
```
Will man den Wert von einem Signal verändern, muss man die Set-Methode von diesem aufrufen. Hier innerhalb von der Funktion eines [[Events, Output]].
```TypeScript
export Class UserComponent {
	selectedUser = signal("Max Mustardman")

	onSelectUser() {
		this.selectedUser.set("Adam Apfel")
	}
}
```
Um den Wert eines Signals abzufragen, wird dieses wie bei [[Dynamische Daten#String Interpolation]] verwendet. Zusätzlich muss das Signal aber wie eine Funktion aufgerufen werden.
```HTML
<span>{{ selectedUser() }}</span>
```
## Alternativ mit 'update' verändern
Alternativ zur 'set()'-Methode gibt es die 'update()'-Methode, welche den Signal-Wert ebenfalls verändert. 'update()' ist komplizierter als Set, eignet sich aber besser für inkrementelle Veränderungen, da es den bisherigen Signalwert als Funktionsparameter mitgibt:
```TypeScript
this.detailsVisible.update((oldSignalValue: boolean): boolean=>{  
  return !oldSignalValue;  
})
```
Diese Funktion flippt die Boolean "detailsVisible". "oldSignalValue" ist der vorherige Wert dieser Variable. Durch die Mitgabe der vorherigen Werte ist 'update()' sehr mächtig!
## Signale mit computed Values
Wenn ein Signal zur Berechnung eines anderen Wertes verwendet wird, muss sich dieser Wert mit der Veränderung des Signals updaten. 
### Warum
Wenn wir ein Signal haben, das innerhalb von einer anderen Variabel oder zur Berechnung einer anderen Variabel verwendet wird, müssen wir die 'computed'-Variabel von Angular verwenden. So wird der berechnete Wert vom Signal-Wert abhängig gemacht und neu berechnet, wenn sich der Wert des Signals ändert.
### Wie
```TypeScript
export class UserComponent {  
    selectedUser = signal(DUMMY_USERS[randomIndex]);  
    imagePath = computed(() => 'assets/users/' + this.selectedUser().avatar);  
}
```
Dass 'imagePath' vom Wert von 'selectedUser' abhängig ist, müssen wir mit 'computed()' definieren.
# Signal Lifecycle
Wenn man auf den Wert eines Signals reagieren will, muss man die 'effect()'-Methode verwenden. Mehr dazu gibt es im Kapitel [[Component Lifecycle#Signal Change Detection]]!