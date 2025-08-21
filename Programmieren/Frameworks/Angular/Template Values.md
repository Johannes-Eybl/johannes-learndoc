#JavaScript #frontend #angular 
# Template Values
Jeden Wert als einzelne Variabel in [[Two Way Binding und Formulare]] einzuspeichern wird schnell unübersichtlich. Es ist einfacher, die Werte mit onSubmit zu übertragen:
```HTML
<form (ngSubmit)="onSubmit(titleInput.value)">  
	<input name="title" id="title" #titleInput/>  
	<button>Submit</button>  
</form>
```
So kann der Wert 'titleInput' innerhalb von TypeScript verwendet werden:
```TypeScript
@Component({ ... })  
export class NewTicketComponent {  
  onSubmit(titleElement: string) {  
    console.log(titleElement.value;)  
  }  
}
```
Durch Template Values kann man einfach auf DOM-Elemente zugreifen. Man muss dem Element eine Value mit einem Hashtag hinzufügen: ```<div #myTemplateValue></div>```.
Nun kann auf dieses Element über seine Template Value zugegriffen werden. 
## Wie Template Values ausserhalb von Funktionen aufrufen?
Mithilfe von '@ViewChild' kann man Template Values auch ausserhalb von Funktionen aufrufen, die sie als Parameter aufnehmen.
```TypeScript
@Component({ ... })  
export class NewTicketComponent {  
  @ViewChild('form') form?: ElementRef<HTMLFormElement>;  
  
  onSubmit(title: string, ticketText: string) {  
    console.log(title)  
    console.log(ticketText);  
    this.form?.reset();  
  }  
}
```
Der Parameter, den '@ViewChild' aufnimmt, kann entweder ein String mit der Template Value oder Typ der Component-Klasse, auf die zugegriffen werden soll, sein.

Das ganze kann auch auf Signalen basierend abgerufen werden:
```TypeScript
@Component({ ... })  
export class NewTicketComponent {  
  //@ViewChild('form') form?: ElementRef<HTMLFormElement>;  
  private form = viewChild<ElementRef<HTMLFormElement>>('form');  
  
  onSubmit() { 
    this.form()?.nativeElement.reset();  
  }  
}
```
## Mehrere Components aufrufen
Man kann anstatt  '@ViewChild' auch mehrere Elemente mit '@ViewChildren' aufrufen.
```TypeScript
@ViewChildren(ButtonComponent) buttons?: ElementRef<ButtonComponent>[];
```
'buttons' ist ein Array aller 'ButtonComponent'-Elemente.
# Projizierte Elemente aufrufen
```HTML
<label>{{ label }}</label>  
<ng-content select="input, textarea"/>
```
Wie kann man auf den Input und die Textarea zugreifen?
Anstatt '@ViewChild' zu verwenden, muss man '@ContentChild' bzw. '@ContentChildren' verwenden. Diese Funktionen funktionieren ähnlich wie '@ViewChild', aber haben einen anderen Syntax:
```TypeScript
@Component({ ... })  
export class ControlComponent {  
  @ContentChild('input') private control?: ElementRef<HTMLInputElement>  
}
```
Auch '@ContenChild' kann auf Signalen basierend umgesetzt werden:
```TypeScript
@Component({ ... })  
export class ControlComponent {  
  private control = contentChild<ElementRef<HTMLInputElement>>('input');
}
```