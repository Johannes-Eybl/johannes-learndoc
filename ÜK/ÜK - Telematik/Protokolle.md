#ÜK
#telematik 
Siehe [[Protokolle Cheatsheets]]
# Layer-7-Protokolle

## Http & Https

Diese beiden Protokolle sind das Hyper Text Transfer Protocol. Es wird verwendet, um Daten auf der Anwendungsschicht (7) über ein Rechennetz zu übertragen.

- Http → Nutzt Port 80
- Https → Nutzt Port 443

Die beiden Protokolle ähneln sich stark, sie sind beide auf Layer 7 und nutzen TCP für den Transport der Daten.

## FTP

FTP steht für File Transfer Protocol. Es wird verwendet, um Dateien von PC zu PC zu senden. 

FTP nutzt Port 20 & 21. Es verwendet TCP für den Transport und liegt auf der Anwendungsschicht.

## Emails

### SMTP

Smtp steht für Simple Mail Transfer Protocol. Es wird beim Versenden von Emails verwendet. Anders als andere Ports verwendet SMTP zwei verschiedene Ports - Port 25 und Port 587.

SMTP befindet sich auf dem Anwendungslayer und verwendet TCP für den Transport.

### POP3 & POP3s

Das Post Office Protocol wird verwendet, damit ein Client Emails von einem Server abholen kann. Dieses Protokoll gilt heutzutags als veraltert und wurde von IMAP abgelöst.

POP3 und sein sicherer Bruder POP3s verwenden die Ports 110 und 995. Es befindet sich auf dem Application Layer und verwendet TCP

### IMAP & IMAPS

Das Internet Message Protocol ist die modernere Version von POP3 und wird quasi für den gleichen Zweck verwendet. Es erlaubt verschiedenen Clients, die Nachrichten eines Accounts auf einem Mailserver zu lesen. IMAP verwendet Port 143 und IMAPS verwendet Port 993. Beide Protokolle befinden sich auf dem Anwendungslayer (7).

## DNS

Das Domain Name System ist dazu da, Namen in IP-Adressen aufzulösen und umgekehrt. Es verwendet UDP und ist auf dem siebten Layer. Port 53

## SSH & Telnet

SSH und Telnet werden beide für Remote Terminals verwendet, wobei Telnet im Gegensatz zu SSH nicht verschlüsselt ist. Beide Protokolle verwenden Port 23, TCP und befinden sich auf dem Application Layer.

## SNMP

Das Simple Network Management Protocol wird dazu verwendet, um von einem zentralen Gerät aus mehrere Netzwerkkomponenten überwachen und steuern zu können.

SNMP verwendet Port 161, UDP und befindet sich auf dem Anwendungslayer

## SIP

Das Session Initiation Protocol wird verwendet, um Sitzungen zwischen zwei Geräten aufzubauen. Es verwendet Port 5060 und 5061 für die gesicherte Version.

## RTSP

Das Real Time Streaming Protocol erlaubt zwei Computern Audiovisuelle Dateien miteinander zu teilen. Es verwendet Port 554 und befindet sich auf dem Anwendungslayer.

## NTP

Das Network Time Protocol wird für die Zeitsyncronisation zwischen Computern verwendet. Benutzen tut es Port 123, UDP und Layer 7 des OSI-Modells (Anwendungslayer).

## SMB

Der Server Message Block ist ein Protokoll für Datei-, Druck und weitere Serverdienste in Rechennetzen. Es verwendet den Port 445 und befindet sich auf dem fünften Layer (Session Layer).

## TCP & UDP

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

## ICMP

Das Internet Control Message Protocol befindet sich auf dem dritten Layer und und wird zum Austausch von Informations- und Fehlermeldungen verwendet. Der Hauptzweck von ICMP ist herauszufinden, ob Daten ihr Ziel rechtzeitig erreichten wie beispielsweise beim Ping.

ICMP befindet sich auf dem Dritten Layer (Network Layer) und verwendet aus diesem Grund auch keine Ports. 

## ARP

Das Adress Resolution Protocol wird dazu verwendet, IP Adressen zu MAC-Adressen aufzulösen. Es befindet sich auf dem Layer 2 des OSI-Modells (Data-Link-Layer)