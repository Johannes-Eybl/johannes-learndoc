#linux
# Entstehung
Linus Torvalds ist der Urvater von Linux. Sein Betriebssystem nannte er zu Beginn (1991) Frax oder Buggix, da er nice dachte, dass es von grossem Interesse sein würde. Er gab die Quellcode einem Freund um ihn auf seinem FTP-Server zu veröffentlichen. Dieser fand die Namenswahl von Linus nicht optimal und machte kurzerhand einen mit aus Linus und Unix. So entstand Linux :-)

Zuerst wurde nur der Kernel, später aber dann das ganze Betriebssystem als Linux bezeichnet. 1992 wurde es offiziell unter der GNU GPL Lizenz veröffentlicht. Der Kern wurde in C geschrieben und ist verfügbar unter https://kernel.org. Teilprozesse, die schneller abgearbeitet werden können, sind in Assembler geschrieben. Es ist wichtig zu beachten, dass der Kernel alleine nicht lauffähig ist. Damit man ein Betriebssystem hat, braucht es ein Kernel, Hilfs-Software und Anwendungsprogramme.

Es gibt gratis Linux-Versionen wie Mint, Ubuntu oder Debian. Dann gibt es noch kommerzielle Versionen wie RedHat Enterprise oder Oracle Enterprise, die man kaufen muss aber dafür Dinge wie 24/7 support haben.

Linux funktioniert unter der GPL (General Public License)-Lizens und der Quelltext von Weiterentwicklungen muss unter der gleichen Lizens veröffentlicht werden.

# Distributionen
Es gibt ganz viele unterschiedliche Linux Versionen. Hier spricht man von Distributionen. Es ist grundsätzliche allen möglich ein eigenes Linux (Distribution) aufzubauen. 

### **Was ist eine Linux Distribution?**

Verschiedene Varianten des Linux-Betriebssystems, die sich in Funktionen, Anwendungsbereichen und Zielgruppen unterscheiden. Eine Distribution besteht aus dem Kernel (der alleine nicht lauffähig ist), Hilfsprogrammen und Anwendungsprogrammen. Sie werden durch Projekte, Stiftungen und Unternehmungen Zusammengestellt. 
Einige Distributionen sind: 
ubuntu, xubuntu, debian, suse, CentOS, SteamOS, Mint, ZorinOS, zentyal, Archlinux, gentoo Linux, fedora, manjaro, redhat 

### **Welche Distributionen sind die wichtigsten bzw. grössten?**

Die grössten und wichtigsten Linux Distributionen sind zum Beispiel Android, Debian, ubuntu und Archlinux. 

### **Wie funktioniert die Linux Lizenzierung?**

GPL (General public License) Version 2 
Es ist alles frei verfügbar → der Quelltext von Weiterentwicklungen muss freigegeben werden. 

### **Wo wird Linux eingesetzt?**

Desktop, Server, Smartphone, Supercomputer, Cloud Provider, Industrie, Unterhaltungselektronik, Netzwerkgeräte

# Partitionierung

Mit Partitionierung kann man ein Speichermedium wie zb. HDD oder einen USB-Stick in mehrere unabhängige Speicherabschnitte einteilen. Jeder Abschnitt kann sein eigenes Dateiensystem enthalten. Für verschiedene Verwendungszwecke gibt es verschiedene Dateiensysteme. 
## Vor- und Nachteile
### Vorteile
- Logische Trennung von OS und Daten
- Datensicherheit
- Verwendung unterschiedlicher Dateiensysteme
### Nachteile
- Erweiterung und Verkleinerung ist komplex und nicht immer möglich
## Partitionierung auf Linux

Auf Linux werden Datenträger mit Buchstaben unterschieden. Zum Beispiel verwendet man /dev/sda und /dev/sdb und /dev/sbc.

Einzelne Partitionen auf diesen Datenträgern werden mit Zahlen unterschieden. Das könnte so aussehen:

/dev/sda1 und /dev/sda2 

Neue Partitionen werden mit `fdisk` angelegt

Neue Filesystems werden mit `mkfs` angelegt

Mit `mount` werden Partitionen in Order eingehängt

Mit `umount` wird ausgehangen

# Wichtige Standard-Ordner
- /dev       Gerätedateien (DEVices)
- /etc        Editable Text Configuration (Konfigurationsdateien)
- /home    Verzeichnisse
- /tmp       Von allen Benutzern zugängliches temporäres Verzeichnis
- /var         Dateien, welche sich ändern. Zb. Logs / DBs
- /media    Verzeichnis für eingesteckte Geräte wie USB oder DVDs
- /mnt        Verzeichnis für eingesteckte Geräte wie USB oder DVDs
# Rechte
Die Rechte-Notation funktioniert mit dem Kürzel rwx (read-write-execute) und kann in binär (zb. 110 oder 101) und damit auch mit Zahlen zwischen 1 und 7 angegegegegeben werden.

Zu jeder Datei werden Rechte an Nutzer, Nutzergruppen und alle Anderen vergeben. Die Rechte sind nach dem Schema rwx (read-write-execute) aufgebaut, was als Text, aber auch als Binär- oder Dezimalzahl dargestellt werden kann. Die Rechtenotation einer Datei bzw. eines Ordners wird in 9 Chars dargestellt (3 mal rwx). 3 für den Eigentümer, 3 für die Gruppe und 3 für Sonstige

- `chmod [DATEINAME]` ändert die Zugriffsrechte
    - `chmod u=rwx [DATEINAME]` für User
    - `chmod g=rwx [DATEINAME]` für Gruppen
    - `chmod o=rwx [DATEINAME]` für Others
    - `chmod a=rwx [DATEINAME]` für all
- `chown [BENUTZER] [DATEINAME]` ändert den Benutzer
- `chgrp [GRUPPE] [DATEINAME]` ändert die Gruppe
- Mit `-R` kann man sich auf alle Dateien in einem Ordner beziehen
# SSH
Auf Standardinstallationen ist SSH nicht installiert. Man muss es zuerst installieren mit `sudo apt install ssh`.
## Mit SSH verbinden
- `ssh meinePcIp`
## Von SSH trennen
- `exit`
## Automatisches einloggen einrichten
Mit `ssh-copy-id` kann man das Passwort für die SSH-Maschine permanent einspeichern. Dann kann man sich direkt mit dem ssh-Befahl einloggen.
## Dateien von SSH-Verbindung zu lokaler Maschine kopieren
`scp -P PORT USER@IP:PATH_TO_DIR_OR_FILE PATH_TO_SAVE_TO_ON_LOCAL_MACHINE`
`scp` steht für Secure Copy.
## Grafische Oberfläche via SSH
Mit `ssh -X` kann man über SSH auch Programme starten, die ein Fenster öffnen.
## Berechtigungen über SSH manipulieren
Man kann innerhalb der Datei, in der der Publickey gespeichert wird, definieren, was ein über SSH verbundener User machen soll. 
Innerhalb von "authorized_keys" am Anfang hinzufügen:
```
command="some command"
```
# Aliasse
Ein Alias ist eine Abkürzung für einen einzelnen Befehl. Gespeichert werden Aliasse in der Datei `.bash_aliases`, welche beim Systemstart aus der Datei `.bashrc` geladen wird.
```
# Alias setzen
alias myAliasName="mein Befehl"

# Alias löschen
unalias myAliasName
```
# User
User gibt es, damit verschiedene Benutzer jeweils ihr persönliches Umfeld haben und diese mittels Berechtigungen voneinander abgeschottet werden können. Es gibt “echte Benutzer”, die für Menschen die sich einloggen gedacht sind und es gibt Systembenutzer, die von Programmen benötigt werden (wie z.B Webserver). 
## Root
`root`ist ebenfalls ein User. Er hat die UID=0 und die GID=0
## User Hinzufügen
- `useradd [Nutzername]`
- Setzt nur den Benutzernamen und kein Passwort
- Mit mehreren Parametern anpassbar
- Für Skripts geeignet

- `adduser`
- Setzt Passwort und andere Informationen
- Nicht für Skripts geeignet
## User löschen
- `userdel`
- `deluser`
## Passwort wechseln
- `passwd [Nutzername]`
Ändert das Passwort des bestimmten Nutzers. Root/Sudo kann auch Passwörter von anderen Nutzern anpassen.
# Gruppen
## Erstellen und löschen
- `addgroup [GroupName]`: Eine leere Gruppe wird hinzugefügt 
- `delgroup [GroupName]`: Löscht die gewählte Gruppe 
## Nutzer zu Gruppen hinzufügen
- `usermod -a -G [GROUP] [USER]`: Fügt einen Nutzer einer Gruppe hinzu 
- `adduser [USER] [GROUP]`: Fügt auch einen User einer Gruppe hinzu, kann aber auch einen neuen Nutzer erstellen
In der Datei `/etc/group` kann man sehen, welche User und Gruppen es gibt, sowie auch deren Zugehörigkeit.
# Berechtigungen
## Berechtigungen einstellen
`sudo chmod 770 `-> Gibt Usern und Gruppen alle Rechte

Bei Linux gibt es 3 sets von "Read, Write, Execute". Diese drei Sets stehen für die Rechte von Usern, Gruppen und Anderen

| RWX  | RWX   | RWX   |
| ---- | ----- | ----- |
| User | Group | Other |
Um rechte zu verändern, werden Zahlen verwendet. "7" steht zB. dafür, dass man lesen, schreiben und executen kann. Die Zahl ist die Summe der unten stehenden Zahlen, welche man verwendet.

| 4   | 2   | 1   |
| --- | --- | --- |
| R   | W   | X   |
## Besitzer einstellen
`sudo chown root:GRUPPE ORDNERPFAD`

# IP von Webseite finden
`nslookup WEBADRESSE` zeigt einem die Adresse von dem Server, der über den Browser mit dem Namen der Webadresse erreichbar ist.