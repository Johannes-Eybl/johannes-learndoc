#linux
# Datei- und Verzeichnisoperationen

---

- `ls`: Auflisten von Dateien und Verzeichnissen
    - `ls -l`: Ausführliche Liste
    - `ls -a`: Alle Dateien anzeigen, inklusive versteckter Dateien
- `cd [Pfad]`: In ein Verzeichnis wechseln
    - `cd ..`: Ein Verzeichnis zurück
    - `cd ~`: Zum Home-Verzeichnis
- `mkdir [Name]`: Neues Verzeichnis erstellen
- `rmdir [Name]`: Leeres Verzeichnis löschen
- `touch [Dateiname]`: Leere Datei erstellen
- `cp [Quelle] [Ziel]`: Datei oder Verzeichnis kopieren
    - `cp -r`: Verzeichnis rekursiv kopieren. Der Inhalt des Ordners wird mitkopiert.
- `mv [Quelle] [Ziel]`: Datei oder Verzeichnis verschieben/umbenennen
- `rm [Dateiname]`: Datei löschen
    - `rm -r`: Verzeichnis rekursiv löschen
    - `rm -f`: Ohne Rückfrage löschen
- `grep [Suchtext] [Datei]`: Text in Dateien suchen
    - `grep -r`: Rekursiv in Verzeichnissen suchen
    - `grep -c`: Vorkommnisse des Suchbegriffs zählen
- `cat [Dateipfad]`: Inhalt einer Datei ausgeben

---

# Texteditoren
## Nano
- **`nano [Dateiname]`**: Datei mit Nano-Editor öffnen
    
- **`Ctrl + O`**: Datei speichern
- **`Ctrl + X`**: Nano schließen
- **`Ctrl + W`**: Text suchen
- **`Ctrl + A`**: Zum Anfang der Datei
- **`Ctrl + E`**: Zum Ende der Datei
- **`Ctrl + K`**: Aktuelle Zeile löschen
## Vi
Dies ist nur eine grobe Zusammenfassung. Eine ausführliche Beschreibung befindet sich im [[VI  Cheatsheet]]
- **`vi [Dateiname]`**: Datei mit Vi-Editor öffnen
### Normaler Modus
Wenn man Vi startet, befindet es sich im normalen Modus. In diesem Modus kann man shortcuts verwenden, aber keinen Text eintippen.
- **`:w`**: Datei speichern
- **`:q`**: Vi schließen
- **`:wq`**: Speichern und schließen
- **`:q!`**: Ohne Speichern schließen
- **`/[Suchtext]`**: Text suchen
### Einfügemodus
Wenn man `i` drückt, kommt man in den Einfügemodus (insert mode). Dann kann man Text ganz normal eintippen. 
### Befehlsmodus
Wenn man `esc` und danach `:` klickt, öffnet sich eine Befehlszeile, in die man verschiedene Befehle eintippen kann;

---


# APT
- **`apt [Aktion]`**: Paketverwaltung (Debian/Ubuntu)
    - **`apt update`**: Paketliste aktualisieren
    - **`apt upgrade`**: Installierte Pakete aktualisieren
    - **`apt install [Paketname]`**: Paket installieren

---

# Wichtige Symbole

- **`> [Dateiname]`**: Ausgabe in Datei umleiten (überschreiben)
- **`>> [Dateiname]`**: Ausgabe an Datei anhängen
- **`|`**: Ausgabe eines Befehls als Eingabe für einen anderen verwenden (piping)
- `*` bedeutet Null oder mehr Zeichen
- `?` bedeutet ein Zeichen
- `[ ]` bedeutet eine Range von Zeichen, zb [1-3]

---

# Benutzer und Gruppen
- `su - [Benutzername]`: Set User - mit Benutzernamen anmelden

- `adduser [Benutzername]`: Neuen Benutzer hinzufügen
- `deluser [Benutzername]`: Benutzer löschen
- `passwd [Benutzername]`: Passwort ändern

- `groups`: Zeigt die Gruppen an, zu denen der aktuelle Benutzer gehört
- `group [USERNAME]`: gibt die Gruppen, in denen ein User ist
- `sudo usermod -aG [Gruppe] [Benutzername]`: Benutzer zu Gruppe adden

---
# Hardware
- `systemctl poweroff`: System ausschalten
- `systemctl reboot`: System neu starten

- `df` → Freien Speicher gemounteter Partitionen anzeigen
- `du` → Belegten Speicher eines Ordners, Unterordners und Dateien anzeigen
- `top` → Linux Programm, das dem Windows-Taskmanager entspricht. Es zeigt die aktuellen Prozesse und deren Leistungsverbraucht an.
- `ps -ef` → Process Status. Zeigt alle aktuellen Prozesse an
- `lspci` und `lsusb` → Listet alle PCI- bzw alle USB-Geräte auf. Mit `lspci | less` kann man es übersichtlicher darstellen lassen.
- Unter /var/log kann man die Logs von Linux finden
- `journalctl` → Zeigt die Logs des Systems an
- `free -h` → Zeigt den RAM an
- `netstat -an` → Zeigt die Netzverbindungen des PCs an
- `tcpdump` → Zeigt die sichtbaren Datenpakete auf der Netzkarte an
- `nice -n [Nummer] [Befehl/Programm]` → Mit dem nice-Befehl kann man die Priorität von Prozessen für den CPU verändern. Es gibt eine Range zwischen -20 (Schnell) und 19 (Langsam). Der Befehl am Schluss der Nice-Eingabe steht für ein Programm oder einen Befehl, was mit dem angegebenen niceness-Level ausgeführt wird.
- `kill -9 [ProcessId]` → Beended einen Prozess, der mit seiner ID angegeben wurde.
---
# Rechte

- `chmod [Berechtigungen] [Datei/Verzeichnis]`: Dateiberechtigungen ändern
- `chown [Benutzer]:[Gruppe] [Datei/Verzeichnis]`: Besitzer und Gruppe ändern
---
# Shortcuts
- `ctrl-a`: zum Anfang der Zeile springen
- `ctrl-e`: zum Ende der Zeile springen
- `ctrl-r`: Befehls-History durchlaufen
