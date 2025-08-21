#ÜK
#telematik
# Netzplan

## Lernziele:

- Den Unterschied zwischen einem schematischen und einem geographischen Netzplan kennen
    - Geographischer Netzplan → Zeigt auf einer Karte, wo welche Geräte physisch vorhanden sind. Zb. ein Gebäudeplan mit eingetragenen PCs und Kabeln.
    - Schematischer Netzplan → Ist eine technische Übersicht und zeigt die Funktion des Netzes und dessen Komponenten. Wird bei der Planung verwendet und ist nützlich zur Fehleranalyse
- Die wichtigsten Netzwerkkomponenten repetieren
    
    ![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%208.png)
    
- Wissen, wozu Netzpläne dienen und welche Zusammenhänge sie aufzeigen
    - Netzpläne dienen einerseits der Planung und andererseits der Wartung/Reparatur von Systemen. Mit Netzplänen kann man einfacher Fehler ermitteln und darauf schliessen, welche Komponente disfunktional ist.
- Verschiedene Beispiele von Netzlplänen kennen und wissen, worauf zu achten ist, um einen eigenen Netzplan mit Visio zu zeichnen
- Einen eigenen Netzplan nach Vorgaben planen und zeichnen

# Protokolle

[Protokolle Cheatsheets](Protokolle%20Cheatsheets.md)

Protokolle sind eine Festlegung von Standarts und Konventionen für eine reibungslose Datenübertragung. Kommunikation kann nur funktionieren, wenn jede Kommunikationsart ein Protokoll hat, an das sich alle halten.

## Ports & Sockets

Ports erlauben einem Server, mehrere Verbindungen zu haben.  IP-Adresse und Port werden gemeinsam zum Socket. Sockets sind Schnittstellen zu der Anwendungsschicht (OSI 5-7) im TCP/IP und werden sowohl von UTP als auch von TCP verwendet (OSI 4).

Auch beim Absenden von Daten wird ein Port verwendet, welcher meist dynamisch ist. Netz-Applikationen und Protokolle haben aber einen eigenen Port, welcher reserviert ist. ZB. hat HTTP den Port 80 und HTTPS Port 443.

### Port-Zuweisungen

- 0 - 1023 → Well known Ports
- 1024 - 49151 → Registred Ports
- 49152 - 65535 → Dynamic & Private Ports

## UDP (User Datagram Protocol)

UDP wurde für Geschwindigkeit entwickelt, dafür ist die Zuverlässigkeit und die Vollständigkeit nicht optimal. Ausserdem hat UDP einen kleinen Overhead, das bedeutet es braucht weniger Daten für das Protokoll an sich. Es bietet einen Zustellungsservice für Datagramme, tut Verbindungen aber weder prüfen noch herstellen!

### Nachteile:

- Es wird nicht garantiert, dass ein Paket ankommt
- Es wird nicht garantiert, dass Pakete in richtiger Reihenfolge ankommen

### Vorteile:

- Es ist schneller als TCP
- UDP wird eingesetzt, wenn Geschwindigkeit wichtiger ist als Vollständigkeit oder Zuverlässigkeit

### UDP-Header

![Untitled](Untitled%201%205.png)

## TCP (Transmission Control Protocol)

TCP ist für Zuverlässigkeit entwickelt worden. Es bestätigt, dass ein Paket angekommen ist und erhält die Verbindung, bis es explizit beendet wird.

### Nachteile:

- Es ist langsamer als UDP
- Generiert viel nicht durch Daten nutzbaren Traffic. Das liegt daran, dass der Header sehr viel Platz braucht, welcher dann nicht für Daten verwendet werden kann.

### Vorteile:

- Dass ein Paket ankommt wird garantiert
- Die Reihenfolge der Pakete ist garantiert
- Das Protokoll kann den Fluss der Daten anpassen (Bandbreite, Verlässlichkeit etc.)

### TCP-Header

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%202%201.png)

Der TCP-Header ist deutlich schwerer als derjenige vom UDP-Protokoll

- Source Port (16bit) → Gibt an, von welchem Dienst auf einer höheren Schicht die Daten stammen.
- Destination Port (16bit) → Gibt an, an welchen Dienst die Daten weitergereicht werden.
- Header Länge (4bit) → Gibt an, wie viele 32-Bit-Wörter dieser umfasst
- Flags (12bit) → Im Moment 8 bit, bedeutet dass 8 Flags definiert sind
- Febstergrösse → Es wird festgelegt, wie viele Bytes ein Gerät noch empfangen kann
- Prüfsumme → Lässt Tests zur Überprüfung der Daten zu
- Dringlichkeitszeiger → Wird benötigt, wenn die Flag für hohe Dringlichkeit gesetzt wurde und gibt an, die Daten angezeigter Länge sofort zu verarbeiten
- Optionen → maximale Grösse für TCP-Segmente definiert, der Rest wird mit Nullen aufgefüllt.

## Three-Way-Handshake

Der Three-Way-Handshake wird vom TCP-Protokoll verwendet umd eine fixe Verbindung aufbauen zu können.

1. Der Sender sendet eine Synchronisationsanforderung (SYN) mit Sequenznummer
2. Der Empfänger sendet eine Synchronisationsbestätigung (Acknowledgement (ACK)) mit empfangener Sequenznummer um 1 erhöht. Gleichzeitig fordert der Empfänger eine Synchronisation an, die auch eine Nummer enthält
3. Im letzten Schritt übermittelt der Sender eine Bestätigung. Dieses Paket enthält die eigene Synchronisationsnummer und die Bestätigungsnummer.
4. Am Schluss haben Sender und Empfänger eine Sequenznummer mit Bestätigung.

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%203%201.png)

# DNS

DNS steht für Domain Name System und ist einer der wichtigsten Netzwerkdienste im Internet. Er löst Namen in IP-Adressen auf und umgekehrt.

Aufbau →Hierarchisch strukturierte Datenbank. Namenserver verwalten nur einen kleinen Teil der gesamten Namensräume.

TLD → Top Level Domain

FQDN → Fully Qualified Domain Name (Kompletter Domainname wie zB. www.de.wikipedia.org)

Die Verwaltung einer Top-Level-Domain erfolgt zentral über eine jeweils zuständige Behörde (www.nic.ch in der Schweiz). Die Beantragung einer TLD erfolgt über autorisierte Registrare.