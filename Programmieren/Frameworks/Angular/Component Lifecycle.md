#angular  
#JavaScript 
#frontend 
# Übersicht
Der Lifecycle von Components in Angular besteht aus drei Phasen:

1. Erstellung
	- Der Component wird konstruiert und initialisiert
	- Input-Werte werden empfangen
2. Change Detection (Active Life)
	- Der Component reagiert auf Veränderungen der Inputs
	- Eigene Checks und Updates werden verarbeitet
	- Content und View werden initialisiert und verarbeitet
	- Der Component wird anhand des States geupdated
3. Destruction
	- Cleanup wird gemacht
	- Subscriptions werden geschlossen
	- Der Component wird von der DOM entfernt.

Im Verlauf dieser drei Phasen werden verschiedene eingebaute Funktionen getriggert, die man mit eigenen Funktionen verknüpfen kann.
# Erstellung / Start
Um bei der Erstellung eines Components Code auszuführen, gibt es zwei Möglichkeiten; den Constructor und 'ngOnInit'.
Der Constructor sollte nur für kleine Tasks wie das Setup von Variablen verwendet werden. 'ngOnInit' ist die Methode, die zum Setup des Components von Angular empfohlen wird.
## Constructor
Kann fürs einfache Setup verwendet werden. Wird ausgelöst bevor Angular richtig involviert ist. Kann genutzt werden, um Klassenvariabeln zu generieren oder um Dependencies zu injecten.
```TypeScript
constructor(private service: MyService) {
  this.localProperty = 'default';
}
```
Die Constructor-Methode ist nicht Teil von Angular, sondern wird von JavaScript unterstützt. Aus diesem Grund wird empfohlen, stattdessen [[#ngOnInit]] zu verwenden.
## ngOnInit
Wird ausgelöst, wenn Angular den Component bereits ready gemacht hat. Ist dadurch geeignet für Dinge wie HTTP-Calls, DOM-Requests oder Zugriff auf '@Input'-Werte.
```TypeScript
ngOnInit() {
  this.service.getData().subscribe(data => {
    this.data = data;
  });
}
```
Um die Implementation von 'ngOnInit' zu vereinfachen, wird empfohlen, der Klasse 'implements OnInit' hinzuzufügen.
```TypeScript
export class ServerStatusComponent implements OnInit {}
```
Dadurch zwingt Angular diese Klasse dazu, die Methode zu enthalten und gibt einen Fehler aus, wenn das nicht der Fall ist. Man kann die Methode auch ohne dieses Interface implementieren, doch bekommt keinen Fehler wenn etwas falsch ist.
## ngAfterViewInit
Wird ausgelöst nachdem Angular die View des Components und seiner Kinder initialisiert hat. Wird genutzt, um einen [[Component]] mit [[Template Values]] zu verarbeiten.
```TypeScript
@Component({ ... })  
export class NewTicketComponent implements AfterViewInit {  
  // `@ViewChild('form') form!: ElementRef<HTMLFormElement>;`
  private form = viewChild<ElementRef<HTMLFormElement>>('form');  
  
  ngAfterViewInit(): void {  
    console.log(this.form()?.nativeElement)  
  } 
}
```
Würde man in [[#ngOnInit]] versuchen, auf [[Template Values]] zuzugreifen, hätte man keine Garantie, dass diese noch verfügbar sind. Aus diesem Grund gibt es 'ngAfterViewInit'.
## ngAfterContentInit
Entspricht [[#ngAfterViewInit]], nur dass es erst getriggert wird, nachdem Angular den projizierten Content inserted hat.
Diese Methode wird nur ein Mal ausgelöst, wenn Angular den externen Content in den Component projiziert hat. 
Da sie nur ein Mal ausgelöst wird, sollte sie nur für ein Setup verwendet werden, das vom projizierten Content abhängig ist.
"Der Content wurde eingefügt - jetzt sollte xyz gemacht werden".

# Change  Detection / Active Life
## ngOnChanges
Diese Methode wird ausgelöst, wenn eine '@input'-Variabel einen neuen Wert von ihrem Parent erhält. 
```TypeScript
ngOnChanges(changes: SimpleChanges) {  
  console.log('ngOnChanges');  
  console.log(changes);  
}
```
Das 'simpleChanges'-Objekt, welches die Methode als Parameter bekommt, etnhält die folgenden Attribute:
- currentValue -> der aktuelle, neue Wert
- firstChange -> die initial-Value
- previousValue -> Der vorherige Wert. 'undefined' bei der ersten Änderung.
## Signal Change Detection
Wenn man auf die Änderung des Wertes eines Signals reagieren will muss man die 'effect()'-Methode im Konstruktor definieren. Sie erstellt eine Subscription zum verwendeten Signal und löst die gegebene Methode bei Änderungen des Signalwertes aus.
```TypeScript
@Component({ ... })  
export class ServerStatusComponent implements OnInit {  
  currentStatus = signal<'online' | 'offline' | 'unknown'>('online');  
 
  constructor() {  
    effect(()=>{  
      console.log(this.currentStatus());  
    })  
  }    
}
```
## afterNextRender
Wird _ein Mal_ nach der nächsten Änderung _irgendwo_ auf der Seite getriggert. Wird häufig verwendet um mit der DOM zu interagieren, wenn sie das erste Mal geladen wird.
```TypeScript
constructor() {  
  afterNextRender(()=>{  
    console.log('after next render');  
  })  
}
```
## afterRender
Wird jedes Mal ausgeführt, wenn sich _Irgendetwas irgendwo_ auf der Webseite ändert! Nützlich, um auf _jedes_ DOM-Update zu reagieren, zb. um das Layout neu zu berechnen.
```Typescript
constructor() {  
  afterRender(()=>{  
    console.log('after render');  
  });  
}
```
> [!WARNING] afterNextRender und afterRender sind erst ab Angular 16 verfügbar!!! 

# Destruction
## ngOnDestroy
```TypeScript
ngOnDestroy() {  
  console.log('ngOnDestroy');  
}
```
Diese Methode wird bei der Zerstörung des Components ausgelöst. Es gibt eine moderne Alternative zu ngOnDestroy, bei der man die 'DestroyRef'-Klasse importiert und deren 'onDestroy()'-Methode verwendet:
```TypeScript
private destroyRef = inject(DestroyRef)  

this.destroyRef.onDestroy(()=>{
  console.log("destroyed ref")
})
```
Die 'destroyRef.onDestroy()'-Methode wird häufig verwendet, wenn man mit einem [[Observable]] arbeitet, um Subscriptions zu beenden.

