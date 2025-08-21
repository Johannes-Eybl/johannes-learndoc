Beim Unit-Testing mit Angular kann man verschiedene Bereiche der Applikation testen:
- **Component**
- **Pipe**
- **Service**
- **Inputs**
- **Injections**
# Warum
Warum testet man Applikationen? Es gibt drei Hauptgründe für das Nutzen von Tests in Angular:
- Die Applikation vor fehlerhaften Änderungen schützen
- Das Verhalten des Codes analysieren (erwartetes und unerwartetes Verhalten)
- Designfehler aufdecken
# Wie
Die default-Testdatei in einem neuen, von der [[Angular-CLI]] erstellten Projekt sieht so aus: 
```TypeScript
import { TestBed } from '@angular/core/testing';  
import { App } from './app';  
  
describe('App', () => {  
  beforeEach(async () => {  
    await TestBed.configureTestingModule({  
      imports: [App],  
    }).compileComponents();  
  });  
  
  it('should create the app', () => {  
    const fixture = TestBed.createComponent(App);  
    const app = fixture.componentInstance;  
    expect(app).toBeTruthy();  
  });  
  
  it('should render title', () => {  
    const fixture = TestBed.createComponent(App);  
    fixture.detectChanges();  
    const compiled = fixture.nativeElement as HTMLElement;  
    expect(compiled.querySelector('h1')?.textContent).toContain('Hello, testing-lernen');  
  });  
});
```
## 'beforeEach'
Hier wird definiert, was vor jedem Test gemacht werden soll. Auch wenn die Tests häufig nach einander durchgeführt werden, sind sie unabhängig von einander und beeinflussen sich _nicht_ gegenseitig.

In diesem Fall wird der Component, welcher getestet werden soll ('appComponent') importiert.
## 'it'-Blöcke
Jeder einzelne Test wird innerhalb von einem 'it'-Block geschrieben.
Am Anfang des Blocks steht eine Beschreibung des Tests bzw. der Name des Blocks.
Am Schluss von jedem Block steht ein 'expect' - hier wird definiert, welches Verhalten von dem getesteten Component erwartet wird.
# Tests ausführen
Mit dem Befehl 'ng test' werden die Tests des Projekts automatisch durchgeführt. Es wird ein Browser geöffnet, der die Ausgabe des Tests anzeigt, welche man ebenfalls in der Konsole erkennen kann.

Der folgende Codeblock ist ein Beispiel für verschiedene Tests:
```TypeScript
describe('Component: User', () => {  
  beforeEach((() => {  
    TestBed.configureTestingModule({  
      imports: [ UserComponent, CommonModule ],  
    }).compileComponents()  
  }))  
  
  it('should create', () => {  
    let fixture = TestBed.createComponent(UserComponent);  
    let app = fixture.debugElement.componentInstance  
    expect(app).toBeTruthy();  
  })  
  
  it('should use the username from the service', () => {  
    let fixture = TestBed.createComponent(UserComponent);  
    let app = fixture.debugElement.componentInstance;  
    let userService = fixture.debugElement.injector.get(UserService);  
    fixture.detectChanges();  
    expect(userService.user).toEqual(app.user.name)  
  })  
  
  it('should display the user name if user is logged in', ()=>{  
    let fixture = TestBed.createComponent(UserComponent);  
    let app = fixture.debugElement.componentInstance;  
    app.isLoggedIn = true;  
    fixture.detectChanges();  
    let compiled = fixture.debugElement.nativeElement;  
    expect(compiled.querySelector('p').textContent).toEqual(app.user.name)  
  })  
  
  it('shouldnt display the user name if user is not logged in', ()=>{  
    let fixture = TestBed.createComponent(UserComponent);  
    let app = fixture.debugElement.componentInstance;  
    app.isLoggedIn = false;  
    fixture.detectChanges();  
    let compiled = fixture.debugElement.nativeElement;  
    expect(compiled.querySelector('p').textContent).not.toContain(app.user.name)  
  })  
});
```
- 'should create' -> Testet, ob der Component initialisiert werden kann
- 'should use the username from the service' -> Vergleicht den Namen vom Service mit dem Namen im Coponent
- 'should display the user name if user is logged in' -> Setzt die 'loggedIn'-Variabel auf 'true' und ruft die 'detectChanges'-Methode auf, um zu testen, ob der Nutzername darauf angezeigt wird.
# Async Tasks testen
Um Applikationen mit asynchronen Tasks zu testen (die auf Server zugreifen), muss man asynchrone Tests schreiben.
## spyOn()
Das Problem mit API-Relevanten Tests ist, dass sie auf den Server zugreifen wollen. Beim Testen will man nicht die ganze Zeit Server-Requests machen. Darum gibt es im Testing-Framework von Angular eine Möglichkeit, den Output von Server-Requests zu faken!
Diese Möglichkeit ist eine Methode namens 'spyOn':
```TypeScript 
let spy = spyOn(dataService, 'getDetails')
	.and.returnValue(Promise.resolve('Data'))  
```
'spyOn' ersetzt den Output einer Methode mit einem Output, der selbst definiert ist. 
'dataService' ist der Service, dessen Methode gefaked wird.
'getDetails' ist der Name der Methode, die gefaked werden soll.
'.and.returnValue()' definiert den Wert, der zurückgegeben werden soll.
## detectChanges()
Nachdem man mit 'spyOn()' definiert hat, welche Daten der Component bekommen soll, muss man noch dessen [[Component Lifecycle]] starten. Zwar hat man mit 'createComponent()' bereits einen Component bekommen, aber dessen [[Component Lifecycle]] wurde noch nicht gestartet.
Das bedeutet, dass 'ngOnInit()' und weitere Methoden des [[Component Lifecycle]] noch nicht getriggert worden sind.
Mit 'detectChanges()' startet man den [[Component Lifecycle]]!
## tick()
Wenn man mit 'fakeAsync()' arbeitet, laufen Timer nicht in Echtzeit. Stattdessen muss man Angular sagen, wann es die Zeit vorspulen muss..
Hier kommt 'tick()' ins Spiel - es sagt Angular, dass es die Zeit vorspulen soll und alle timer/tasks triggern muss.
Genau genommen werden Macro- und Mircotasks in einer fakeAsync-Zone gespeichert. 'tick()' triggert all diese Tasks.
Im unteren Beispiel wird mit 'tick()' die Promise-Resolution, die in [[#spyOn()]] definiert wurde, getriggert.
## Der fertige async-Test
Dieser Test kombiniert die Funktionen, welche die letzten Abschnitte beschrieben haben.
```TypeScript
it('shouldnt fetch data successfully if not called asyncronously', fakeAsync(() => {  
    let fixture = TestBed.createComponent(UserComponent);  
    let app = fixture.debugElement.componentInstance;  
    let dataService = fixture.debugElement.injector.get(DataService);  
    let spy = spyOn(dataService, 'getDetails')  
      .and.returnValue(Promise.resolve('Data'));  
    fixture.detectChanges();  
    tick()  
    expect(app.data).toBe('Data')  
  })  
)
```
# Isolierte und nicht-Isolierte Tests
Wenn man Pipes und andere einfache Funktionen verwendet, die einen Input nehmen und einen bestimmten Wert ausgeben sollten (zB. String transformations), kann man diese sehr einfach testen.

Wenn man beispielsweise die folgende Pipe, die nur eine Funktion hat, testen will:
```TypeScript
@Pipe({  
  name: 'reverse'  
})  
export class ReversePipe{  
  transform(value: string){  
    return value.split("").reverse().join("");  
  }  
}
```
Dann kann man das mit dem folgenden Test machen:
```TypeScript
import {ReversePipe} from './reverse.pipe';  
  
describe('Component: user', ()=>{  
  it('should create an instance', () => {  
    let reversePipe = new ReversePipe();  
    expect(reversePipe.transform('Hello')).toEqual('olleH');  
  })  
})
```
Dieser Test ist an sich nicht mal von Angular abhängig, da nur der Output von einer einzelnen Funktion (also keine komplexe Angular-Interaktion) getestet wird.

Dieser Test ist ein **Isolierter Test**.
Um herauszufinden, ob ein Test isoliert ist oder nicht, muss man sich fragen, ob der Test von anderen Components oder Angular-Features abhängig ist.

Wenn ein Test nicht isoliert ist, gibt es Werkzeuge wie das 'TestBed'-Objekt, welches beim Setup eines Tests hilft. Ausserdem kann man für nicht-isolierte Tests auch 'fakeAsync' und 'tick' verwenden. Es gibt zudem noch viele weitere Tools, welche beim Testen helfen können.
# Components mit Inputs testen
Es gibt viele Components, die einen Input erwarten. Wenn man ihnen keinen gibt, schlägt der Test fehl.

