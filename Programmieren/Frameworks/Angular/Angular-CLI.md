#JavaScript 
#angular 
#frontend 
# Installation
Mit ```npm install -g @angular/cli``` wird die CLI in der Kommandozeile installiert. 
## Abhängigkeiten
Die Angular-CLI ist von NodeJS und Npm abhängig. Angular an sich benötigt diese Tools nicht, doch um die Cli zu verwenden, muss man sie installiert haben.
# Projekt erstellen
```Bash
ng new first-angular-app
```
# Projekt starten
Das im letzten Schritt erstellte Projekt kann mit ```npm start```oder mit ```ng serve```gestartet werden. 
Bei Veränderungen im Code wird die Webseite automatisch aktualisiert.

Die Webseite ist auf ```localhost:4200``` verfügbar.
# Generieren von [[Component]] mit der [[Angular-CLI]]
Man kann auch mit der [[Angular-CLI]] Components erstellen. 
```Bash
ng generate component NAME
```
oder 
```Bash
ng g c NAME
```
Diese zwei Befehle erstellen beide einen neuen Component mit dem Namen NAME. Dazu wird ein neuen NAME-Ordner generiert, in dem die drei Dateien des Components gespeichert sind.
