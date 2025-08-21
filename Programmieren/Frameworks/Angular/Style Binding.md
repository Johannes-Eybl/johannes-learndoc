#angular 
#JavaScript 
#frontend 
So wie beim [[Class Binding]] und beim [[Dynamische Daten#Property Binding]] kann man in Angular auch Style Binden und konditional machen.
## Mit Objekt
```HTML
<div [style]="{  
  'font-size': '64px',  
}">
```
Anstatt eines Strings kann bei '64px' auch eine TypeScript-Expression stehen, die einen validen CSS-Wert generiert (zB. eine Funktion).
## Ohne Objekt
Wenn man nur einen einzelnen Style definieren, kann man dies auch ohne Objekt machen:
```HTML
<div [style.fontSize]="'64px'">
```
Auch hier kann anstatt "64px" ein dynamischer Wert mit TypeScript generiert werden.
Da "64px" an sich kein valides TypeScript ist, wurde es in diesem Beispiel nochmal in Anführungszeichen gesetzt, um als String ausgewertet zu werden.