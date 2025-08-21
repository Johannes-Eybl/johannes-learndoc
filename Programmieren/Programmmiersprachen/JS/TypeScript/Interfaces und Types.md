#typescript
#programming 
Mit Types und Interfaces kann man die Struktur eines Objekts ein Mal definieren und immer wieder neu verwenden.

Mit Types:
```TypeScript
type User = {
	name: string,
	avatar: string
}

@Component({...})  
export class UserComponent {  
     @Input() user!: User; 
}
```
Bzw mit Interfaces:
```TypeScript
interface User {
	name: string,
	avatar: string
}

@Component({...})  
export class UserComponent {  
     @Input() user!: User; 
}
```
Es gibt keinen nennenswerten Unterschied zwischen Types und Interfaces.
# Auslagern in andere Dateien
Da man die Strukturen von manchen Objekten immer wieder verwendet, macht es Sinn, diese in andere Dateien auszulagern.

Namensschema: 'name.model.ts'

Achtung: Das Interface bzw der Type muss mit 'export' markiert sein, damit er in anderen Dateien genutzt werden kann!
