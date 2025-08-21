#schule 
#m117

# Lernziele

- Die verschiedenen Arten von Ressourcen in einem Peer-To-Peer-Netzwerk aufzeigen
- Den Unterschied zwischen den einzelnen Systemadmin-Tools erklären
- Dateifreigaben anzeigen lassen, einrichten und über das Netzwerk nutzen
- Benutzer und Gruppen auf einem Host einrichten

# Netzwerkressourcen

Netzwerke erlauben es verschiedenen Nutzern, gemeinsame Ressourcen zu verwenden. 

Typische Netzwerkressourcen sind Dateisysteme, Drucker und Datenbanken. Diese können sich entwerder im lokalen Netzwerk oder im Internet befinden. Für die Nutzung von Ressourcen wird das *SMB Server Message Block*-Protokoll verwendet.

# Sysadmin-Tools

## GUI

Für Anfänger geeignetes Interface → Mit Maus und Tastatur die Einstellungen bearbeiten.

## CMD (Windows) / Shell (Linux)

Weiterentwickeltes DOS-Interface. Textbasiert.

## Power-Shell (Windows) / Bash (Linux)

Basiert auf dem Befehlssatz des CMD, geht aber noch tiefer. Profi-Tool.

Linux hat standartmässig Bash und nicht (!) die Shell. Bash steht für “Bourne Again Shell”

# Datei-/Ordnerfreigaben

## Freigegebene Ordner ansehen

### Windows GUI

“Computerverwaltung” → Freigegebene Ordner → Freigaben

Man kann “Computerverwaltung” bei der Suche mit dem Suchbegriff “compmgmt” finden.

### CMD / PowerShell

`net share` zeigt die gleichen Informationen wie “Computerverwaltung” im GUI

## Ordner Freigeben

### Windows GUI

Auf gewünschten Ordner rechtsklicken → Eigenschaften → Freigabe → Freigabe / Erweiterte Freigabe.

### CMD / PowerShell

`net share [NAME]=[PFAD]` gibt dem gewünschten User den gewünschten Ordner frei. 

`net share sh-public=c:\data` → Gibt dem User sh-public den Ordner C:\data frei.

## Netzlaufwerk verbinden

### Windows GUI

Explorer öffnen → “Dieser Computer” → “Netzlaufwerk verbinden” (Obere Leiste)

Wichtig ist, im Menü “Verbindung bei Anmeldung wiederherstellen” anzuklicken, damit die Verbindung dauerhaft bleibt.

### CMD / PowerShell

`net use [BUCHSTABE]:[PFAD]` → Verbindet sich mit einem Laufwerk auf gewünschtem Pfad. Dieses Laufwerk hat dann den Namen vom gewählten Buchstaben.

`net use x:\\192.168.110.10\sh-proj` → Macht einen Netzwerkordner, der X heisst und dessen Pfad “\\192.168.110.10\sh-proj” ist.

### Linux

![Untitled](Schulmodule/M117%20-%20Netzwerke/Fotos%20&%20PDFs/Untitled%203.png)

# Benutzer einrichten

## Windows GUI

“Computerverwaltung” → Lokale Benutzer und Gruppen → Benutzer

Man kann “Computerverwaltung” bei der Suche mit dem Suchbegriff “compmgmt” finden.

## CMD / PowerShell

`net user [NUTZERNAME] [PASSWORT] /add`  

`net user weber sml12345 /add /fullname:"Hannes Weber"` (Der letzte Teil nach “/add” ist optional)

## Linux

`sudo adduser [NUTZERNAME]` löst einen Dialog aus, in dem man Gruppe, PW und weiteres eingeben kann. Darauf muss man den PC neu starten.

# Gruppen einrichten

## Windows GUI

“Computerverwaltung” → Lokale Benutzer und Gruppen → Gruppen

Man kann “Computerverwaltung” bei der Suche mit dem Suchbegriff “compmgmt” finden.

## CMD / PowerShell

`net localgroup [GROUP_NAME]` → Zeigt die Mitglieder der Gruppe an

`net localgroup [GROUP_NAME] /add` → Fügt eine neue Gruppe hinzu

`net localgroup [GROUP_NAME] [USER_NAME] /add` → Fügt einen Nutzer der Gruppe hinzu

`/add` ist nicht die einzige Option, es gibt auch `/delete`