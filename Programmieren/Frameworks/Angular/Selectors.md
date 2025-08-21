#JavaScript 
#angular 
#frontend 
Mit Selektoren kann man bestehende HMTL-Elemente erweitern. Ein Selector ist das Element, mit dem man einen Component einbindet.
```TypeScript
@Component({  
  selector: 'button[appButton]',  
  standalone: true,  
  imports: [],  
  templateUrl: './button.component.html',  
  styleUrl: './button.component.css'  
})  
export class ButtonComponent {  
  
}
```
In diesem Fall wird ein normaler HTML-Button erweitert. Will man diesen Component nun nutzen, muss man das auf folgende Weise machen: 
```HTML
<button appButton></button>
```
# Welches Problem lösen Selectors
Will man beispielsweise einen eigenen Button implementieren, der dann überall genutzt werden soll, ist es einfacher, einen normalen Button mit Selektor zu verwenden, als ständig einen ganzen ("normalen") Component zu nutzen.