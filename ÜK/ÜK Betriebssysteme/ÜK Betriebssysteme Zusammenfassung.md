#ÜK
#betriebssysteme

# Prüfung Teil 1 (Schriftlich)

## Bewertung

- Externe und interne Schnittstellen identifizieren und benennen

![Untitled](ÜK/ÜK%20Betriebssysteme/PDFs&Fotos/Untitled%201.png)

![Untitled](ÜK/ÜK%20Betriebssysteme/PDFs&Fotos/Untitled%201%201.png)

![Untitled](ÜK/ÜK%20Betriebssysteme/PDFs&Fotos/Untitled%202.png)

- Festplatten werden angeschlossen mit SATA oder m.
- Lizenzen für bestimmte Anwendungszwecke evaluieren Unterscheiden und Erkennen der Rechte und Plichten der unterschiedlichen Lizenzierungsarten
- Lizenz- und Aktivierungsmöglichkeit für Private und eine für Unternehmen. Privat: Windows Schlüssel oder Digitale Lizenz, Business: MAK oder eigener Aktivierungs-Server KMS
- Closed-Source
    - Windows, MacOS
    - Programmcode ist nur im Besitz des Herstellers
    - Hersteller schreibt vor, was mit Software gemacht werden darf
- Open-Source
    - Linux
    - Programmcode ist frei zugänglich
    - Grundsätzlich gratis, verdient Geld durch Support oder Spenden
    - Lizenz schreibt vor was mit Code gemacht werden darf
    - Unterschiedliche Lizenzen: GPL, BSD
        - BSD ist grundsätzlich open source aber man kann es closed machen
        - GPL ist immer open source
- Vorgehensweise zum Testen einer neu eingerichteten Internetverbindung
    - In der Suchleiste “Netzwerkverbindung” eingeben, oder in Einstellungen auf Netzwerk und Internet Einstellung
    - Netzwerkverbindung testen
        - ipconfig
            - anzeigen des aktuellen Status der Netzwerkadapter
        - ping
            - Erreichbarkeit einer Adresse im Netz
        - nslookup
            - Auflösen von namen in IP
    - Ip Adressen (Eindeutige Identifikation)
        - Private Adressen
            - 192.168.0.0
            - 172.16.0.0
            - **10**.0.0.0
            - 169.245.0.0
    - Netzmaske
        - Definiert die Grösse des eigenen Netzes. Je mehr 255, deste kleiner das Netz
    - DNS
        - Namensauflösung zu IP
    - DHCP
        - Dynamische IP-Zuweisung
    - Standart-Gateway
        - Notwendig, um Kommunikation mit anderen Netzen zu betreiben
- Worauf ist zu achten bei dem ergonomisch ausrichten
    - Stuhl einstellen
    - Tischhöhe einpassen
        - Bewegungsraum
        - Tischhöhe
            - Ellbogen = Tischhöhe + Tastaturhöhe
    - Überblick
        - Bildschirmoberkante 10cm unter Augenhöhe
    - Sehdistanz zum Bildschirm: Ausgestreckte Hand
    - Beleuchtung
        - Indirektes Licht (Fenster an Seite), Keine Reflektion
    - (Bewegungs)-Pausen
    - Lärmpegel nicht zu hoch halten (55db)
- Auswahl, Wartung und Kompatibilität von Speichermedian und Datensystemen, auch zwischen den Betriebssystemen
    - Speichermedianauswahl
        - Externe Festplatte
        - USB Flash Laufwerk
        - SD karten
        - HDD und SSD
            - SSD ist schneller und verwendet Flash-Speicherchips, sie haben keine rotierenden Festplattenscheiben, SSDs sind leise
            - HDDs verwenden rotierende Festplattenscheiben, HDDs erzeugen hörbare Geräusche
    - Dateisystem
        - Unterschiedliche Stärken/Schwächen/Anwendungen
        - Dateisysteme für lokale Datenträger und für Netzwerkspeicher-Zugriff
        - Regelt die Ablageorganisation und Möglichkeiten
        - FAT32
            - Vorgänger: Fat12. Fat16
            - Kompatibel mit **allen Betriebssystemen**
            - Standard bei USB Sticks
            - **MAX Dateigrösse: nur 4GB**
        - NTFS
            - Proprietäres Dateisystem von Microsoft
            - Standard auf allen **Windows Geräten**
            - Nur bei Windows
        - exFAT
            - Nachfolger von FAT32
            - Bringt viele Vorteile von NTFS, jedoch KEINE Rechteverwaltung
                - Schlanker als NTFS
                - Kompatible mit **Windows, MacOS und Linux**
        - ext4
            - Vorgänger: ext2, ext3
            - Dateisystem aus der Linux Welt
            - Standard auf vielen **Linux Systemen**
        - APFS
            - Proprietäres Dateisystem von **Apple**
            - Standard auf MacOS
        - swap
            - Spezialdateisystem nur für Auslagerungsspeicher
            - wird nicht klassisch formatiert (mkfs) sondern mit “mkswap”
            - wird nicht klassisch eingehängt (mount), sondern mit “swapon” bzw. “swapoff”
            - ist für **Linux**
        - NW-Dateisystem: SMB 3.x
            - Netzwerkdateisystem
            - Ursprünglich aus der **Windows** Welt
            - Heute gängig auch für Cross-Plattform (**Linux**, **macOS**)
        - NW-Dateisystem: NFS
            - Netzwerkdateisystem
            - ursprünglich von Sun (UNIX)
            - Offener Standard
            - Vor allem  unter **Linux** (und **macOS**, VMware) verbreitet
            - Typisch Berechtigungen eher auf Host- als auf User-Ebene, daher eher für Einbindung von Shares auf Servern als direkt bei Clients
        - ReFS
            - Neues Dateisystem von **Microsoft**
            - Ausgelegt auf Schadenserkennung
            - Soll von NTFS im Windows Serverbereich ablösen
    - Wartung
        - Regelmäßige Sicherungen sind entscheidend, unabhängig vom Speichermedium und Betriebssystem.
        - Überprüfen und aktualisieren Sie regelmäßig Ihre Dateisysteme und Softwaretreiber, um Kompatibilitätsprobleme zu vermeiden.
- Partitionierung und Formatierung von Speichermedien
    - Partitionierung bezieht sich auf die Aufteilung eines physischen Speichermediums in separate logische Abschnitte, die als Partitionen bezeichnet werden. Diese Partitionen können als separate Laufwerke betrachtet werden und dienen dazu, Daten zu organisieren und verschiedene Betriebssysteme oder Dateisysteme zu unterstützen.
    - Formatierung: NTFS, FAT32, exFAT, ext4, etc.
    - Schritte zur Partitionierung und Formatierung
        - Bei Windows: auf der “Datenträgerverwaltung”
        - Bei Linux: Datenträger und Partitionen stehen als Gerätedatei zur Verfügung
            - Dateiträger: z.B. /dev/sda
            - Partitionen: z.B. /de/sda1, /dev/sda2
        - Partitionen erstellen: fdisk oder cfdisk
        - Dateisysteme anlegen: **mkfs**
    - Partitionstabellen / Partitionsschema
        - MBR (benutz von BIOS)
            - Älter, “Legacy”
            - Mit viele OS kompatibel
            - Nur 4 primäre Partitionen
        - **GPT (benutz von UEFI)**
            - Nachfolger von MBR
            - Unterstützung seit Windows XP 64Bit
            - Max partitionsgrösse:18 Exabyte
            - Unbegrenzt (Windows:128)

## Praxisbezug

- Kennt verschiedene Lizenz Bestimmungen und kann entscheiden welche für den vorgegebene Zweck die ideal ist.
    - Open Source-Lizenzen: Diese Lizenzen erlauben die Verwendung, Modifikation und Weiterverbreitung von Software oder Inhalten unter bestimmten Bedingungen. Beispiele hierfür sind die GPL
    - Proprietäre (closed-source) Lizenzen: Diese Lizenzen beschränken normalerweise die Nutzung, Modifikation und Weiterverbreitung von Software oder Inhalten. Sie werden häufig von Unternehmen für ihre eigenen Produkte verwendet und erfordern normalerweise eine Lizenzgebühr oder eine Zustimmung des Lizenzgebers.
- Kennt Vorgehensweisen um die korrekte WAN-Anbindung zu testen.
    - Der Ping-Test ist eine einfache Möglichkeit, die Konnektivität zu überprüfen. Verwenden Sie das Ping-Tool, um einen entfernten Host (z. B. einen Webserver) anzupingen. Ein erfolgreicher Ping zeigt an, dass Datenpakete erfolgreich zwischen Ihrem Standort und dem entfernten Host gesendet und empfangen werden können
    - “ping” in der Eingabeaufforderung oder im Terminal, gefolgt von der IP-Adresse oder dem Hostnamen.
        
        ```bash
        ping [www.google.com](http://www.google.com/)
        ```
        
- Kennt den Vorgang um Effizienz Fehler zu finden und zu beheben
    - Systematisches Vorgehen
        - Fehler lesen
        - Vom Allgemeinen ins Detail
        - Abschlussverfahren anwenden
    - Tools: Ressourcenmonitor, Systeminformationen, Leistungsüberwachung, Ereignisanzeige
    
    Verschiedene Fehler
    
    **1. Hardware-Fehlermeldungen:**
    
    - **Festplattenfehler:** Diese Meldungen deuten auf Probleme mit der Festplatte hin, wie zum Beispiel defekte Sektoren, fehlerhafte Lese- / Schreibvorgänge oder Festplattenversagen.
    - **Speicherfehler:** Hierbei handelt es sich um Fehler im RAM (Random Access Memory), die zu Abstürzen oder unerwartetem Verhalten führen können.
    - **Temperatur- und Überhitzungsfehler:** Diese Meldungen warnen vor einer Überhitzung von Komponenten wie der CPU oder der Grafikkarte.
    - **Stromversorgungsfehler:** Diese Fehlermeldungen deuten auf Probleme mit der Stromversorgung hin, wie Spannungsabfälle oder Unterbrechungen.
    - **Peripheriegerätefehler:** Sie können Fehler mit angeschlossenen Geräten wie Druckern, Tastaturen oder Mäusen signalisieren, zum Beispiel wenn ein Treiber fehlt oder veraltet ist.
    
    **2. Betriebssystem-Fehlermeldungen:**
    
    - **Bluescreens (unter Windows):** Diese Meldungen erscheinen in der Regel bei schwerwiegenden Fehlern im Windows-Betriebssystem und werden oft von einem Stop-Fehlercode begleitet.
    - **Kernel-Panics (unter Linux):** Ähnlich wie Bluescreens unter Windows, zeigen sie kritische Fehler im Linux-Kernel an.
    - **Bootfehler:** Diese Meldungen treten auf, wenn das Betriebssystem nicht ordnungsgemäß gestartet werden kann, z.B. aufgrund fehlender oder beschädigter Systemdateien.
    - **Treiberfehler:** Hierbei handelt es sich um Fehler im Zusammenhang mit Hardwaretreibern, die zu Konflikten oder Abstürzen führen können.
    - **Systemwarnungen:** Diese Meldungen weisen auf wichtige Ereignisse oder Probleme hin, die vom Betriebssystem erkannt wurden, z.B. kritisch niedriger Festplattenspeicher oder Überhitzung.
    
    **3. Fehlermeldungen von Anwenderprogrammen:**
    
    - **Anwendungsabstürze:** Diese Meldungen treten auf, wenn ein Anwenderprogramm (z.B. Textverarbeitung, Browser oder Spiele) unerwartet abstürzt.
    - **Anwendungsfehler:** Sie weisen auf Probleme innerhalb einer Anwendung hin, z.B. das Scheitern einer Aufgabe oder die Unmöglichkeit, auf Ressourcen zuzugreifen.
    - **Benutzerinteraktionsfehler:** Diese Meldungen signalisieren Probleme bei der Benutzerinteraktion, wie ungültige Eingaben oder fehlende Dateien.
    - **Konfigurationsfehler:** Hierbei handelt es sich um Fehler im Zusammenhang mit den Einstellungen und Konfigurationen einer Anwendung.
- Kennt Möglichleiten und Lösungen um einen Arbeitsplatz nach ergonomische vorgaben einzurichten
    - Stuhl einstellen, Tischhöhe, Monitorposition, Beinfreiheit, Pausen und Bewegung, Augen pflegen
- Kann geeignete Speichermedien auswählen und diese fachgerecht warten.
    - Festplattenlaufwerke (HDDs und SSDs), USB-Sticks und externe Festplatten, Cloud-Speicher, SD karten
- Kann Speichermedien unter Berücksichtigung der gestellten Anforderungen partitionieren und formatieren
    - Partitionieren eines Speichermediums
        - Sicherung der Daten
        - Öffnen Sie das Partitionierungstool (Bei Windows: Datenträgerverwaltung)
        - Dann Rechtsklick und “Neues einfaches Volumen wählen”
        - Speichermedium auswählen
        - Partition erstellen
        - Übernehmen Sie die Änderungen
    - Formatieren einer Partition
        - Öffnen Sie das Formatierungstool (Datenträgerverwaltung)
        - Wählen Sie die Partition aus
        - Wählen Sie das Dateisystem

# Prüfung Teil 2 (Praktisch)

## Praxisbezug

- PCs auf Energie-Effizienz konfigurieren
    - Einstellungen-System-Leistung-Energieempfehlung
    - Im BIOS
        - Sparoptionen für den Prozess
        - PCIe-karten
        - SATA Anschlüsse
    - Treiber aktualisieren
    - Programme aktualisieren
- Updates von Betriebssystemen und Programmen konfigurieren und überwachen
    - Automatische Updates aktivieren
    - Update-Zeitplan festlegen
- Neue Benutzer erstellen und gewünschte Rechte vergeben
    - Einstellungen-Andere Benutzer-Konto hinzufügen
- Absichern eines ICT Arbeitsplatzes mit entsprechender Software und Konfiguration
    - 
- Netzwerkeinstellungen am PC analysieren konfigurieren
    - 
- Grundlegendes Verständnis des Dateisystems mit Hilfe einer Shell (Linux Shell, Power Shell, CMD, usw.) sowie Anwendung der gängigen Befehle für die Navigation durch das Dateisystem und die Dateiverwaltung oder einer graphischen Oberfläche
    - /=root Folder
    - /bin=Tools, Programme
    - /boot=booten
    - /**dev=Gerätedateien**
    - /**etc=Konfigurationsdateien**
    - /home=Homeverzeichnis
    - /lib=kernel Module
    - /mnt=z.B usb Stick
    - /opt=software von dritten
    - /var=Dateien, welche sich ändern

## Praxisbezug

- Kann Features des Betriebssystem erweitern und einzelne Produkte nach Vorgaben installieren und konfigurieren
    - 
- Kann Netzwerkeinsellungen analysieren und Schlüsse bezüglich Konnektivität daraus schliessen.
    - 
- Findet sich in der Shell zurecht und kann grundlegende Funktionen anwenden
    - 
- Kann bei Performanceproblemen die Ressourcen überprüfen und sie eingrenzen
    - 
- Kann systematisch Fehler eingrenzen und zuordnen
    - 
- Kann sich in einem Datensystem bewegen und Konfigurationen durchführen.
    - 
- Kennt verschiedene Absicherungsmassnahmen und kann entscheiden welche für den vorgegebenen Zweck die ideale ist.
    -