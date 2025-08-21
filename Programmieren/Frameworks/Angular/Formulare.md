#JavaScript #angular #frontend 
Es gibt zwei Weisen wie man mit Formularen umgehen kann:

- Template-Driven Forms -> Einfacher, für kleine Formulare
- Reactive Forms -> Komplexer, für grosse Formulare

Das bedeutet aber nicht, dass man alle Features der einen oder anderen Art von Form benutzen muss. Für kleinere Applikationen ist es möglich, eher einfache und nicht streng gegliederte Forms zu verwenden.
Doch wenn man grössere Applikationen entwickelt, sollte man sich zu Einfachheit an eine der beiden Konventionen halten.

|                      | Template-Driven                                      | Reactive                                                  |
| -------------------- | ---------------------------------------------------- | :-------------------------------------------------------- |
| **Herangehensweise** | Deklarativ - die meiste Logik ist innerhalb vom HTML | Imperativ - die meiste Logik ist innerhalb vom TypeScript |
| **Skalierbarkeit**   | Kleine, simple Formulare                             | Komplexe, dynamische Formulare                            |
| **Testing**          | Schwieriger zum testen, da der Code im HTML lebt.    | Einfach zu testen                                         |
# Template-Driven Forms
## Deklaration
Wenn man eine Template-Driven Form verwendet, erstellt Angular im Hintergrund ein 'FormControl'- und ein 'FormGroup'-Objekt. Diese Objekte müssen mit [[#Reactive Forms]] explizit definiert werden.

Um Angular zu sagen, dass es diese Objekte im Hintergrund erstellen soll, muss man dem Form-Tag folgendes Attribut geben:
```HTML
<form #form="ngForm">
	...
</form>
```
Nun weis Angular, welche Art von Formular verwendet wird. Jetzt werden die mit 'ngModel' versehenden Inputs (nächste Abschnitt) mit dem generierten Form-Objekt verknüpft.
## Inputs definieren
Template-Driven Forms verwenden 'ngModel' im HTML, um ihre Werte mit TS-Variablen zu verbinden. 
```HTML
  <input id="password" type="password" name="password" ngModel/>
```
Achtung - damit man 'ngModel' so verwenden kann, also ohne ```[(ngModel)]="password"``` schreiben zu müssen, muss das Input-Element das Attribut 'name' definiert haben!
## Werte mit TypeScript abfragen
Zunächst muss dem Form-Element eine 'onSubmit'-Variable hinzugefügt werden:
```HTML
<form #form="ngForm" (ngSubmit)="onSubmit(form)">
	...
</form>
```
Darauf kann man diese Methode im Component definieren:
```TypeScript
@Component({ .. })  
export class LoginComponent {  
  onSubmit(formData: NgForm) {
    const enteredEmail = formData.form.value.email;  
    const enteredPassword = formData.form.value.password;

	console.log(formData)
  }  
}
```
Das 'ngForm'-Objekt, welches mit der Funktion weitergegeben wird, enthält alle Input-Werte, die mit 'ngModel' registriert worden sind. Dazu gibt es noch einige weitere Attribute, wie zB. 'touched', das angibt, ob der User das Element verwendet hat.
## Validierung - Regeln festlegen

> [!WARNING] Die folgenden Validierungs-Attribute verhindern _nicht_ das Submitten von Forms!
> Stattdessen ändert es das Form-Objekt, welches bei einer Submission erstellt wird!
> 
> Ist die Form invalid, wird 'form.status' "INVALID" sein!
#### Required
Wie bei normalen HTML-Inputs kann man auch bei einem Template-Driven-Formular einfach den Ausdruck 'required' ins HMTL-Element schreiben:
```HTML
<input id="email" type="email" name="email" ngModel required/>
```
Ohne weitere Änderungen wird hier der vom Browser standardisierte 'required'-Dialog für Formulare verwendet.
#### Email
So wie das Attribut 'required' kann man auch ein 'email'-Attribut zum HTML-Element hinzufügen:
```HTML
<input id="email" type="email" name="email" ngModel email/>
```
Auch hier wird der vom Browser standardisierte Email-Prüfer verwendet!
#### Minimale & Maximale Länge
Will man, dass ein Input eine Mindestlänge hat (zB. ein Passwort), dann kann man diese ebenfalls innerhalb des HMTL-Elements definieren:
```HTML
<input id="password" type="password" name="password" ngModel required minLength="6"/>
```
Auf dieselbe Weise kann man auch die 'maxLength' definieren.
#### Eigener Regex
Man kann auch eigene Regex-Patterns definieren, nach denen Inputs validiert werden sollen:
```HTML
<input id="email" type="email" name="email" ngModel pattern="`@[a-zA-Z0-9.-]+\`"/>
```
### Regeln abfragen
Will man wissen, ob die gesetzten Validierungs-Regeln eingehalten werden, muss man beim Form-Objekt den Status der Form abfragen:
```TypeScript
@Component({ .. })  
export class LoginComponent {  
  onSubmit(formData: NgForm) {  
    if(formData.form.invalid){  
      return;  
    }else{
	    console.log("Form Valid!")
    }
  }  
}
```
Diese Abfrage prüft aber nur, ob die ganze Form valid bzw. invalid ist. Will man wissen, _welcher_ Teil der Form invalid ist, wird es etwas komplizierter:
```TypeScript
for (const name in formData.controls) {
  const control = formData.controls[name];
  if (control.invalid) {
    console.log(name, control.errors);
  }
}
```
## User feedback geben
```TypeScript
@if (email.touched && password.touched && form.form.invalid) {  
  <p class="control-error">  
    Invalid values detected. Please check your input.  
  </p>  
}
```
Dieser Code zeigt nur dann eine Meldung, wenn der Nutzer bereits 'email'- und 'passwort'-Inputs berührt hat und ein Input der Form nicht valid ist.

Doch um 'email' und 'password' als Variablen zu haben, auf die man einfach zugreifen kann, muss man sie erst als [[Template Values]] registrieren.
```HTML
<input id="email" type="email" name="email" ngModel required email #email="ngModel"/>
```
Doch was macht ```#email="ngModel"```genau?
Dieser Syntax sagt Angular, dass diese Template Value mit der ngModel-Instanz des Components verbunden werden soll, anstatt mir dem DOM-Element.
Nur so kann man im oberen TypeScript auf das Attribut 'touched' zugreifen.
## Validierungs-Styling
Bei Input-Elementen, werden dynamisch CSS-Klassen hinzugefügt, wenn sich ihr Status ändert. 
- 'ng-pristine' -> Ob das Element einen Input enthält/empfangen hat
- 'ng-invalid' -> Ob das Element einen validen Input hat
- 'ng-touched' -> Ob der User das Element mindestens angeklickt hat

Zu all diesen CSS-Klassen gibt es noch gegenteilige Klassen wie zb. 'ng-untouched'.

Diese Klassen können ein eigenes Styling bekommen, mit dem die Elemente bei Problemen anders aussehen.
```CSS
input.ng-invalid.ng-touched.ng-dirty {  
  background-color: #fbdcd6;  
  border-color: #f84e2c;  
}
```
## Form resetten
Häufig will man eine Form automatisch leeren, zB. nachdem sie ausgefüllt wurde. Dafür gibt es eine Funktion innerhalb des 'ngForm'-Objekts.
```TypeScript
@Component({ .. })  
export class LoginComponent {  
  onSubmit(formData: NgForm) {  
    if(formData.form.invalid){  
      return;  
    } else {
    formData.form.reset()  
	}
  }  
}
```
## Form-Daten speichern
Damit ein User nach dem Verlassen der Seite nicht von vorne anfangen muss, ist es sinnvoll, die Form-Daten kurzfristig zu speichern.
Dazu wird LocalStorage verwendet:
```TypeScript
private form = viewChild<NgForm>('form');  
private destroyRef = inject(DestroyRef)  
  
constructor() {  
  afterNextRender(()=>{  
    const subscription = this.form()?.valueChanges?.pipe(  
      debounceTime(500),  
    ).subscribe({  
      next: (value) => {  
        window.localStorage.setItem('saved-login-form', JSON.stringify({email: value.email}));  
      }  
    })  
  this.destroyRef.onDestroy(() => subscription?.unsubscribe());  
  })  
}
```
- ```private form = viewChild<NgForm>('form')```-> Nutzt ViewChild (mehr dazu in [[Template Values]]), um auf das 'ngForm'-Objekt zugreifen zu können.
- ```afterNextRender(()=>{...})```-> Siehe [[Component Lifecycle#afterNextRender]]
- ```this.form()?.valueChanges?```-> Observable, das bei Wertänderungen emittet
- ```.pipe(debounceTime(500))```-> Wartet 500ms bevor es das Signal emittet. Verhindert ständiges Emitten während der User tippt.
- ```.subscribe({...})```-> Wenn dir Subscription ausgelöst wird, wir der Inhalt des Email-Feldes im LocalStorage abgespeichert.
## Gespeicherte Daten zum Auffüllen der Inputs verwenden
Um gespeicherte Daten anzuzeigen, muss man den Code im oberen Abschnitt ([[#Form-Daten speichern]]) erweitern.
```TypeScript
constructor() {  
  afterNextRender(()=>{  
    const savedForm = window.localStorage.getItem('saved-login-form');  
  
    if(savedForm){  
      const loadedFormData = JSON.parse(savedForm);  
      const savedEmail = loadedFormData.email;  
      setTimeout(()=>{  
        this.form()?.controls['email']?.setValue(savedEmail);  
      }, 1)  
    }  
  
    const subscription = this.form()?.valueChanges?.pipe(  
      debounceTime(500),  
    ).subscribe({  
      next: (value) => {  
        window.localStorage.setItem('saved-login-form', JSON.stringify({email: value.email}));  
      }  
    })  
  this.destroyRef.onDestroy(() => subscription?.unsubscribe());  
  })  
}
```
- Zunächst wird das 'saved-login-form'-Item aus dem Storage gezogen und geprüft, ob es 'truthy', also nicht leer, ist.
- Darauf wird das gewünschte Attribut 'email' aus dem Datenobjekt gezogen.
- Nun kann der Wert der 'email'-Control der Form gesetzt werden. Da das Element beim laufen vom Constructor noch nicht vorhanden ist, muss man mit 'setTimeout' einen Tick warten, damit es funktioniert.
# Reactive Forms
Einer der wichtigsten Unterschiede zwischen Template-Driven- und Reactive-Forms ist, dass das Setup des Formulars in der Reactive-Form nicht im HTML, sondern innerhalb des TypeScript-Components stattfindet. 
## Deklaration
Um ein Formular innerhalb von TypeScript zu deklarieren, muss man eine Variabel erstellen, die ein neues FormGroup-Objekt trägt:
```TypeScript
form: FormGroup = new FormGroup({})
```
Die Klasse 'FormGroup' benötigt beim Initialisieren eines neuen Objekts ein Konfigurationsobjekt als Parameter, welches verschiedene Key:Value-Paare enthält, die die verschiedenen Controls des Formulars repräsentieren.
```TypeScript
form:FormGroup = new FormGroup({  
  email: new FormControl(''),  
  password: new FormControl(''),  
})
```
Die Werte diese Control-Elemente sind Objekte der Klasse 'FormControl'.
## Form-Objekte mit HTML-Elementen verbinden
Die im letzten Abschnitt definierten Form-Objekte sind noch nicht mit ihren HTML-Elementen verbunden.

Dafür muss man zunächst das Form-Element mit der im letzten Abschnitt definierten Form-Variabel verbinden:
```HTML
<form [formGroup]="form">  
	...
</form>
```
Nun kann man die verschiedenen Inputs der Form mit den im Konfigurationsobjekt verbundenen Attributen verbinden:
```HTML
<form [formGroup]="form">  
	...
  <input id="email" type="email" formControlName="email"/>  
	...
  <input id="password" type="password" formControlName="password"/>  
	...
</form>
```
## Form Submission & Werte abfragen
Wie bei Template-Driven-Forms verwendet man auch bei reaktiven Forms 'ngSubmit':
```HTML
<form [formGroup]="form" (ngSubmit)="onSubmit()">
	...
</form>
```
Nur muss man bei reaktiven Forms keine Werte mitgeben, da die Verbindung der Form zum Code bereits im TypeScript des Component hergestellt ist!
```TypeScript
form: FormGroup = new FormGroup({  
  email: new FormControl(''),  
  password: new FormControl(''),  
})  
  
onSubmit() {  
  const enteredEmail = this.form.value.email;  
  const enteredPassword = this.form.value.password;  
  
  console.log(this.form)  
}
```
Die 'onSubmit()'-Funktion gibt das genau gleiche Form-Objekt (vom Typ 'FormGroup') aus wie im Abschnitt [[#Werte mit TypeScript abfragen]]. Denn im Hintergrund verwendet Angular für das Verarbeiten von Forms die gleichen Objekte wie bei Template-Driven-Forms. Nur das Setup im Projekt ist anders.

Einer der Unterschiede zu Template-Driven-Forms ist, dass der Type der Input-Value bereits im TypeScript vordefiniert ist. Das macht das Abfragen von Werten leichter.
## Validierung -Regeln festlegen
Validierungskriterien werden bei reaktiven Forms innerhalb der TypeScript-Deklaration der Form deklariert.
Bei der Erstellung der 'FormControl'-Objekte wird neben der Default-Value noch ein Konfigurationsobjekt mitgegeben, in welchem die Validierung definiert wird:
```TypeScript
form: FormGroup = new FormGroup({  
  email: new FormControl('', {  
    validators: [Validators.required, Validators.email],  
  }),  
  password: new FormControl('', {  
    validators: [Validators.required, Validators.minLength(6)],  
  }),  
})
```
Zum Attribut 'validators' kann man dem Konfigurationsobjekt noch viele weitere Key:Value-Paare mitgeben, die in diesem Kapitel aber nicht thematisiert werden.
## User Feedback geben
Bei reaktiven Forms sollte man nicht innerhalb vom HTML, sondern im TypeScript abfragen, ob ein Component in Ordnung ist und eine Warnung angezeigt werden sollte:
```HTML
@if(emailIsInvalid){  
  <p class="control-error">  
    Your Email is invalid!  
  </p>  
}  
  
@if(passwordIsInvalid){  
  <p class="control-error">  
    Password is not valid! :(  
  </p>  
}
```
Die Funktion 'emailIsInvalid' und 'passwordIsInvalid' fragt innerhalb vom TypeScript-Component ab, ob der Input in Ordnung ist:
```TypeScript
get emailIsInvalid(){  
  return this.form.controls["email"].touched && this.form.controls["email"].dirty &&  
    this.form.controls["email"].invalid;  
}  
  
get passwordIsInvalid(){  
  return this.form.controls["password"].touched && 
  this.form.controls['password'].dirty &&  
    this.form.controls["password"].invalid;  
}
```
Auch hier fügt Angular den Elementen [[#Validierungs-Styling]] hinzu, welches man in der CSS-Klasse nutzen kann. So ist es sehr einfach, dem Nutzer visuelles Feedback zu geben.
## Custom Validator
Ein eigener Validator ist nichts anderes als eine Funktion, die das Control-Element als Input nimmt und als Output entweder 'null' ausgibt (wenn das Control-Element in Ordnung ist) _oder_ ein Objekt mit Details über den Fehler ausgibt, den die Funktion ermittelt hat.

Im folgenden Beispiel ist eine Funktion, die prüft, ob ein Component ein Fragezeichen enthält:
```TypeScript
function mustContainQuestionMark(control: AbstractControl) {  
  if (control.value.contains('?')){  
    return null;  
  }else{  
    return {doesNotContainQuestionMark: true};  
  }  
}
```
Wenn man diesen Validator nun bei einem Control-Element nutzen will, muss man die Funktion bei der Deklaration der Validators in deren Array einfügen:
```TypeScript
form: FormGroup = new FormGroup({   
  password: new FormControl('', {  
    validators: [Validators.required, Validators.minLength(6), mustContainQuestionMark],  
  }),  
})
```
## Custom Validator mit 2 Controls
Im vorherigen Abschnitt ist beschrieben, wie man ein einzelnes Control-Element mit einem eigenen Validator validieren kann. Doch manchmal will man mehrere, zusammenhängende Controls gleichzeitig validieren. 

Die Lösung für diese Situation sind [[#Nested Form Groups]], denen man einen Validator geben kann, der alle Controls innerhalb der FormGroup betrifft!

Im folgenden Beispiel gibt es ein 'password' und ein 'confirmPassword'-Feld, deren Eingaben abgeglichen werden. 
Zunächst wird eine Validations-Funktion erstellt:
```TypeScript
function equalValues(control: AbstractControl) {  
  const password = control.get('password')?.value;  
  const confirmPassword = control.get('confirmPassword')?.value;  
  
  if(password === confirmPassword) {  
    return null  
  }else{  
    return {passwordsNotEqual: true}  
  }  
}
```
Nun kann man diese Funktion mit der FormGroup verlinken:
```TypeScript
passwords: new FormGroup({  
  password: new FormControl('', {  
    validators: [  
      Validators.required,  
      Validators.minLength(6),  
    ]  
  }),  
  confirmPassword: new FormControl('', {  
    validators: [  
      Validators.required,  
      Validators.minLength(6),  
    ]  
  }),  
}, {  
  validators: [equalValues]  
}),
```
## Async Validator
Async Validators verwendet man beispielsweise wenn man beim Backend fragen muss, ob eine Emailadresse bereits registriert wurde.

Der grösste Unterschied zwischen 'normalen' und asynchronen Validatoren ist, dass async Validators immer ein [[Observable]] zurückgeben. 
```TypeScript
function emailIsUnique(control: AbstractControl) {  
  if(control.value !== 'test@example.com'){  
    return of(null)  
  }else{  
    return of({notUnique: true});  
  }  
}
```
- Anstatt die Value gegen einen String zu prüfen, würde man in einem echten Projekt an der Stelle auf das Backend zugreifen.
- ```of()```gibt ein Observable zurück, das direkt eine Value ausspuckt, die als Argument mitgegeben wurde.

Diesen 'emailIsUnique'-Validator muss man als asynchronen Validator registrieren:
```TypeScript
form: FormGroup = new FormGroup({  
  email: new FormControl('', {  
    validators: [Validators.required, Validators.email],  
    asyncValidators: [emailIsUnique]  
  }) 
})
```
Ist ein asynchroner Validator bei den normalen Validators eingetragen, wird das Element _immer_ als nicht Valid markiert sein! 
## Form-Daten speichern
Damit ein User nach dem Verlassen der Seite nicht von vorne anfangen muss, ist es sinnvoll, die Form-Daten kurzfristig zu speichern.
Dazu wird LocalStorage verwendet:
```TypeScript
ngOnInit(){  
  this.form.valueChanges.pipe(debounceTime(500)).subscribe({  
    next: value => {  
      window.localStorage.setItem(  
        'saved-login-form',  
        JSON.stringify({email: value.email})  
      )  
    }  
  })  
  this.destroyRef.onDestroy(()=>subscription.unsubscribe());
}
```
In dieser Funktion wird eine Subscription erstellt, die bei einer Änderung der Form getriggert wird. 
Die Pipe (mit 'debounceTime') macht, dass die Subscription nur nach 500ms Inaktivität getriggert wird.
## Gespeicherte Daten zum Auffüllen von Inputs verwenden
Um im LocalStorage gespeicherte Daten abzufragen und diese im Formular einzusetzen, muss man diese mit 'window.localStorage.getItem' abfragen. Darauf kann man diese (vorausgesetzt, dass die gespeicherten Daten vorhanden sind) mit 'patchValue' in das Formular einsetzen.
'patchValue' sorgt dafür, dass nur einzelne Werte geändert- und andere Inputs in Ruhe gelassen werden.
```TypeScript
ngOnInit(){  
  const savedForm = window.localStorage.getItem('saved-login-form')  
  
  if(savedForm){  
    const loadedForm = JSON.parse(savedForm)  
  
    this.form.patchValue({  
      email: loadedForm.email,  
    })  
  }
  
  ...
}
```
### Der alternative Weg
Es gibt noch einen alternativen Weg, um gespeicherte Daten ins Formular zu laden.
Dafür muss man _ausserhalb_ des Components die gespeicherten Daten laden:
```TypeScript
let initialEmailValue = ''  
const savedForm = window.localStorage.getItem('saved-login-form')  
if(savedForm) {  
  const loadedForm = JSON.parse(savedForm)  
  initialEmailValue = loadedForm.email  
}
```
Dieser Code wird ausgeführt, sobald die Datei zum ersten Mal im Browser geladen wird (also bevor der Component von Angular initialisiert wird).
Darum kann man in der Definition des Formulars die 'initialEmailValue' als initial value mitgeben:
```TypeScript
form: FormGroup = new FormGroup({  
  email: new FormControl(initialEmailValue, {  
    validators: [Validators.required, Validators.email],  
    asyncValidators: [emailIsUnique]  
  }),
})
```
## Nested Form Groups
Manche Form-Inputs gehören zusammen. Zum Beispiel 'streetName', 'streetNumber' und 'postalCode'. Oder 'username' und 'password'.
Für solche Gruppen kann man verschachtelte Formulare erstellen, die mehrere Inputs bündeln. Dazu verwendet man eine 'FormGroup', die alle zusammengehörenden Inputs enthält. 'FormGroup' ist auch das Objekt, welches das gesamt Formular enthält, doch die Klasse kann auch innerhalb einer anderen 'FormGroup' zur Verschachtelung von Formularen verwendet werden!
```TypeScript
form: FormGroup = new FormGroup({  
  email: new FormControl('', {  
      validators: [  
        Validators.required,  
        Validators.email  
      ],  
    }  
  ),  
  passwords: new FormGroup({  
    password: new FormControl('', {  
      validators: [  
        Validators.required,  
        Validators.minLength(6),  
      ]  
    }),  
    confirmPassword: new FormControl('', {  
      validators: [  
        Validators.required,  
        Validators.minLength(6),  
      ]  
    }),  
  }),
}
  ```
  In diesem Beispiel wird eine Formgroup zur Trennung von 'email' und 'password'-Feldern genutzt.
  Die verschachtelten 'FormControl'-Objekte müssen aber noch mit der HTML-Template verbunden werden! Dafür muss man alle Inputs, die im TypeScript-Component zusammengefasst worden sind, auch im HTML unter einem Div-Tag (auch andere Tags möglich) zusammenfassen und diesen Parent-Tag mit 'formGroupName' mit dem TypeScript verbinden. 
  ```HTML
  <div class="control-row" formGroupName="passwords">  
	  <div class="control">  
	    <label for="password">Password</label>  
	    <input      
	      id="password"  
	      type="password"  
	      name="password"  
	      formControlName="password"  
	    />  
	  </div>   
	  
	  <div class="control">  
	    <label for="confirm-password">Confirm Password</label>  
	    <input      
		  id="confirm-password"  
	      type="password"  
	      name="confirm-password"  
	      formControlName="confirmPassword"  
	    />  
	  </div>
  </div>
  ```
Wenn man nun auf die verschachtelten Controls zugreifen will, ist das etwas komplizierter, als einfach 'this.form.controls' abzufragen. Die verschachtelten inputs sind nun als 'passwords.password' und 'passwords.confirmPassword' abgespeichert.

Darum muss man diese Controls wie folgt ansprechen:
```TypeScript
get passwordIsInvalid() {  
  return this.form.get("passwords.password")?.touched && this.form.get("passwords.password")?.invalid  
}
```
## Radiobutton-Auswahl - Form Arrays
In manchen Formularen will man, dass der User einen oder mehrere zusammenhängende Radiobuttons auswählen kann. Dieses Input-Element gibt es als solches jedoch nicht, weshalb man dieses selber programmieren muss.

Form Arrays sind die beste Lösung für dieses Problem. Man könnte auch mit [[#Nested Form Groups]] arbeiten, doch Arrays sind in diesem Fall besser geeignet.

> [!NOTE] FormArrays werden verwendet, wenn man eine Liste von Components hat und nicht jeden einzelnen Component separat konfigurieren und benennen will
> Stattdessen wird eine Liste an Controls verwendet, die zusammenarbeiten sollen.

Das folgende FormArray befindet sich innerhalb von einem FormGroup-Konfigurationsobjekt und definiert drei FormControls. 
```TypeScript
source: new FormArray([  
  new FormControl(false),  
  new FormControl(false),  
  new FormControl(false),  
]),
```
Wie bei [[#Nested Form Groups]] muss auch hier der Parent (in diesem Fall das FormArray) mit dem Parent der HTML-Template verbunden werden:
```HTML
<fieldset formArrayName="source">
	...
</fieldset>
```
In diesem Fall enthält das 'fieldset' alle drei Radiobuttons, die sich im FormArray befinden.

Jetzt muss noch der Inhalt des FormArrays mit der HTML-Template verbunden werden. Dies wird mit dem 'formControlName' gemacht. Dieser bekommt aufsteigende Zahlen als Value, denn es handelt sich hier ja um ein Array:
```HTML
<fieldset formArrayName="source">  
  <legend>How did you find us?</legend>  
  <div class="control">  
    <input      type="checkbox"  
      id="google"  
      name="acquisition"  
      value="google"  
      formControlName="0"  
    />  
    <label for="google">Google</label>  
  </div>  
  <div class="control">  
    <input      type="checkbox"  
      id="friend"  
      name="acquisition"  
      value="friend"  
      formControlName="1"  
    />  
    <label for="friend">Referred by friend</label>  
  </div>  
  <div class="control">  
    <input      type="checkbox"  
      id="other"  
      name="acquisition"  
      value="other"  
      formControlName="2"  
    />  
    <label for="other">Other</label>  
  </div>
</fieldset>
  ```




  
