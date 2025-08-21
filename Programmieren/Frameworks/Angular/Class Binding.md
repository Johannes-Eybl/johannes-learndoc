#angular 
#JavaScript 
#frontend 
# Einzelne Klassen
Um zb. ein ausgewähltes Element zu markieren, muss man dessen Klasse verändern. Die meisten Webseiten benötigen eine Manipulation von Klassen, um richtig zu funktionieren.
```HTML
<button [class.active]="selected">  
    MyBtn
</button>
```
'selected' ist eine Boolean, welche die Klasse 'class.active' aktiviert oder deaktiviert.
```HTML
<div [class.status]="currentStatus === 'offline'">
```
Dies ist ein weiteres Beispiel von einer Klasse, die nur unter bestimmten Bedingungen zum Element gehört.
# Mehrere Klassen
Manchmal will man nicht nur eine, sondern gleich mehrere Klassen dynamisch hinzufügen. Dafür kann man folgendes Objekt verwenden:
```HTML
<div [class]="{ 
  'status-online': currentStatus === 'online',  
  'status-offline': currentStatus === 'offline',  
  'status-unknown': currentStatus === 'unknown'  
}">
```
Jedes Attribut innerhalb des Objekts ist eine Klasse, die dem Objekt hinzugefügt wird, wenn dessen Value 'true' ist. So können mehrere Klassen dynamisch hinzugefügt werden.
