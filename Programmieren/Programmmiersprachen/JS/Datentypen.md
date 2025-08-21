# Arrays
## Abfragen, ob Variabel ein Array ist
```JavaScript
Array.isArray(myVar)
// Produces true or false
```
## Splice - Elemente hinzufügen oder entfernen
Mit `splice()` kann man Elemente in einem Array hinzufügen, entfernen oder austauschen. 
Mit `toSpliced()` wird ein neues Array erstellt und mit `splice()` wird das bestehende Array verändert.
### Parameter
`splice(start, deleteCount, item1, item2, item3, ...)`

`start` -> Der Index, an dem das Array geändert werden soll. 

`deleteCount`-> Wie viele Elemente im Array vom Start-Index entfernt werden sollen.Wenn DeleteCount 0 oder negativ ist, werden keine Elemente entfernt. In diesem Fall soll mindestens ein neues Element definiert werden. Wird deleteCount nicht definiert, werden alle Elemente ab dem gegebenen Start-Index entfernt.

`item1, item2, etc.` -> Die Elemente, die neu zum Array hinzugefügt werden. Es können beliebig viele Elemente zum hinzufügen angezeigt werden. Werden keine Elemente hinzugefügt, wird `splice()`nur Elemente entfernen.

### Element Löschen
```JavaScript
// Lösche ein Element beim Index "2" des Arrays
myArr = myArr.splice(2, 1)

// Lösche zwei Elemente ab dem Index "5" des Arrays
myArr = myArr.splice(5, 2)

// Alle Elemente ab dem Index "3" entfernen
myArr = myArr.splice(3)
```
### Element austauschen
```JavaScript
// Löscht ein Element bei Index "2" und setzt an dessen Stelle einen neuen Eintrag ein
myArr = myArr.splice(2, 1, "newEntry")
```
### Element einfügen
```JavaScript
// Setzt einen neuen Eintrag beim Index "0" des Arrays und entfernt keinen Eintrag!
myArr = myArr.splice(0, 0, "newEntry")
```
# Object und Dicts
## Übersicht
In JS sind alle Objekte auch Dicts und umgekehrt. Es wird wie folgt defininert:
```JavaScript
let objOrDict = {
	a: "1",
	b: "2",
	c: "3"
}
```
## Alle Keys abfragen
```JavaScript
Object.keys(objOrDict)
// Output: ["a", "b", "c"]
```
## Nach bestimmtem Key fragen
```JavaScript
key in object
```