#ÜK
#telematik

# Wie das Netz entstanden ist

Während dem kalten Krieg wollte man Ressourcen innerhalb der eigenen Kräfte teilen, damit ein Angriff nicht das gesamte Militär lahm legt. Das erste Netzwerk war das ARPANET. Zunächst war dieses nur Militärisch, dann kamen Universitäten dazu und schlussendlich wurde es auch für normale Leute zugänglich.

# Netzwerkausdehnung (xAN)

- PAN (Personal Area Network)
    - Zb. Handy und Bluetooth-Kopfhörer
- LAN (Local Area Network)
    - Netzwerk innerhalb eines Büros oder eines Hauses
- CAN (Campus/City Area Network)
    - Zb. Uni Bern. Ein Netzwerk von der Grösse eines teils der Stadt.
- MAN (Metropolian Area Network)
    - Grösse einer ganzen Stadt. Zb. Vernetzung von Telekommunikationsanbietern innerhalb einer Stadt
- WAN (Wide Area Network)
    - Grösse eines Landes bzw. der ganzen Welt, obwohl dieses dann ein GAN (Global Area Network) wäre.

# Übertragungsarten (Simplex - Duplex)

- Simplex
    - Man kann in nur eine Richtung sprechen
    - Bsp. Radio
- Halb-Duplex
    - Man kann zuhören und sprechen, aber nicht gleichzeitig
    - Bsp. Walkie-Talkies
- Voll-Duplex
    - Man kann gleichzeitig reden und zuhören
    - Bsp. unser Internet

# Kommunikationsrichtung / Übertragunsarten 2 (Broadcast - Multicast - Unicast)

- Unicast
    - Eine Person ansprechen (eins zu eins)
- Multicast
    - Einen Teil einer Gruppe ansprechen (eins zu einige)
- Broadcast
    - Alle Teile der Gruppe ansprechen (eins zu alle)

# Netzwerktopologien (xy-Netze)

## Vollvermaschung

Bei der vollvermaschung ist jedes Gerät mit jedem anderen verbunden.

- Jedes Gerät hat eine grosse Bandbreite zu jedem anderen Gerät im Netzwerk
- Ausfall eines Gerätes oder einer Verbindung hat keinen Einfluss aufs Netzwerk
- Braucht sehr viel Hardware und Kabel - daher teuer.

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%201.png)

## Busnetz

### Vorteile

- Es werden keine weiteren Geräte zur Datenübertragung benötigt
- Ausfall eines Gerätes hat keinen Einfluss aufs Netzwerk
- Geringe kosten, einfache Verkabelung und Erweiterung

### Nachteile

- Daten können leicht abgehört werden
- Eine Störung im Bus kann das ganze Netz lahmlegen
- Störungen sind schwer zu lokalisieren

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%201%201.png)

## Ringnetz

### Vorteile

- Alle Geräte können als Verstärker arbeiten
- Klar definierte Richtung mit Vorgänger und Nachfolger

### Nachteile

- Ausfall eines Gerätes kann das ganze Netz stören
- Hoher verkabelungsaufwand
- Kann leicht abgehört werden

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%202.png)

## Sternnetz

### Vorteile

- Ausfall eines Teilnehmers ohne Folgen für das Netz
- Hohe Übertragungsrate mit Switch möglich
- Einfach erweiterbar, so lange die Zentralreinheit Kapazität hat.
- Leichte Fehlersuche, leicht verständlich

### Nachteil

- Durch Ausfall der Zentraleinheit ist das ganze Netz kaputt
- Die zentrale Einheit kann ein Bottleneck sein

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%203.png)

## Baum

### Vorteile

- Einfache Konstruktion
- Einfach erweiterbar
- Übersichtlich und günstig

### Nachteile

- Bei einem Ausfall eines Vermittlers wird der ganze anhängende Zweig abgeschnitten
- Schwachstelle Networkswich

## Hybride

Die verschiedenen Arten von Topologien kommen auch in kombinierter Struktur vor.

# Protokolle und Schnittstellen

### Protokoll Definition

Um eine reibungslose Kommunikation zwischen verschiedenen Geräten zu ermöglichen, benutzt man Protokolle. Diese geben vor, wie Kommuniziert wird, nicht nur im “sprachlichen” Bereich, sondern auch im Bezug auf Rahmenbedingungen, Ablauf oder den Zeitpunkt der Kommunikation.

### Schnittstelle Definition

Schnittstellen sind einerseits physikalische Verbindungen zweier Systeme (Stecker&Buchse). Andererseits sind Schnittstellen auch digitale Verbindungen zweier Komponenten, also wenn zwei Systeme miteinander “reden”. Das wird auch ein Interface genannt.              Anders formulert sind Schnittstellen die Berührungspunkte von Systemen, die ansonsten unabhängig voneinander arbeiten.

# Schichtenmodelle

Ein Schichtenmodell teilt die Komunikation zwischen Sender und Empfänger in Schichten auf. Die Übertragene Information läuft über diese Schichten hinweg. Jede Schicht gibt die Information an die darüber- oder darunterliegende Schicht weiter. 

## Verschiedene Modelle:

### OSI

![Untitled](Untitled.jpeg)

Mit der Hilfe des OSI-Modells wird die Datenkommunikation in sieben Schichten unterteilt. Jede dieser Schichten kommuniziert nur mit den sich anliegenden Schichten und hat ein eigenes Protokoll für diese Kommunikation. Bei der Versendung von Daten werden die darüber liegenden Informationen nach unten weiter geleitet, nachdem die Informationen des eigenen Protokolls hinzu gefügt wurden. Beim Empfangen von Daten werden bestehende Protokollinformationen verarbeitet und von den Daten entfernt bevor diese an die darüberliegende Schicht weiter geleitet werden. 

Auf dem Weg von Anwendungsschicht des Senders bis zur Anwendungsschicht des Empfängers durchlaufen die Daten also alle sieben Layers zwei mal, zuerst von 7 zu 1 und dann wieder hoch zur Anwendungsschicht des Empfängers. Diese Struktur (von oben runter und dann wieder hoch) nennt man auch Protokollstapel.

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%204.png)

- Steht für  Open System Interconnection

## Genaue Erklärung der 7 Layer

### Aufgabe Physical Layer (1)

Das Physical Layer hat die Verantwortung, digitale Daten physisch zu übertragen, also zB. via Kabel. Es ist das einzige Layer, in dem Informationen lediglich mit einzelnen Bits dargestellt werden. Die Definition der Standarts von physischen Schnittstellen gehören ebenfalls zu dem ersten Layer. Dazu gehören zum Beispiel die Form von Steckern und die Belegung von deren Pins.

### Aufgabe Data Link Layer (2)

Das Data Link Layer hat zwei Aufgaben:

- Das Absichern einzelner Bits durch eine Fehlererkennung. Damit das möglich ist, werden von Layer-2-Protokollen so genannte Prüfsummen generiert. Anhand dieser Nummern können die vom empfangenen Daten kontrolliert werden. Ist ein Fehler vorhanden, werden die Informationen erneut angefordert. Dieses Verfahren nennt man ARQ (automatic repeat request).     Wenn bei einer schlechten Verbindung zu viele Fehler auftauchen kann es jedoch vorkommen, dass die gleichen Daten sehr häufig versendet werden müssen, bis sie korrekt ankommen (ist abhängig von der Menge der Daten)
- Die Zweite Verantwortung des Data Link Layers ist das Zuordnen von Netzwerkknoten zu physischen Adressen. Am Anfang eines Layer-2-Protokolls befinden sich eine Source- und eine Destination-Adresse, diese Adressen werden als MAC-Adressen bezeichnet.

### Aufgabe Network Layer (3)

Die Hauptaufgabe des Network Layers besteht darin, für die korrekte Zustellung der Daten von Sender zu Empfänger zu sorgen. Das Network Layer bekommt beim Senden Daten vom *Transport Layer* (- nr. 4) und muss den richtigen Weg für diese Daten wählen. Die vom *Transport Layer* genommenen und anhand von Protokollen weiterverarbeitete Daten nennt man Datagamme. 

### Aufgabe Transport Layer (4)

Das Transport Layer hat einerseits die Aufgabe, darüber liegenden Applikationen eine Basis für Host-to-Host Verbindungen zu ermöglichen. Während es dem Nutzer am PC so vorkommt, als hätte er eine ständige Verbindung, tut das Transport Layer diese Verbindung tatsächlich öffnen und schliessen, je nach dem ob sie gebraucht wird. Die zweite Aufgabe des Transport Layers ist es, die erhaltenen Daten in richtiger Reihenfolge zu versenden und diese aufzuteilen (segmentieren). Das kann je nach Netzwerkstruktur (Topologie) sehr relevant sein (zB. auch bei Games wie Shootern, wo es sehr präziesen Datenaustausch braucht.). Im Gegensatz zum Session Layer ist das Transport Layer aber nur für die Vermittlung von Daten zuständig, und nicht für das Herstellen der Verbindung zweier Geräte. Es hat ausserdem auch die Aufgabe, die vom oberen Layer erhaltenen Daten aufzuteilen (zu segmentieren), damit diese versandbereit sind.

### Session Layer (5)

Das Session Layer hat die Aufgabe, die Verbindung zwischen zwei Applikationen oder Geräten zu ermöglichen und diese auch wieder zu beenden. Es ist nur für die Verbindungsherstellung und nicht für die Datenübertragung zuständig. Man kann sagen, dass es vor allem (Verbindungen) managed, aber die Arbeit (den Transport) den unteren Layern überlässt.

### Presentation Layer (6)

Das Presentation Layer hat die Aufgabe, Daten in einen Zustand zu versetzen, der von den restlichen Layers verstanden wird. Dazu gehören auch das Verschlüsseln oder Komprimieren von Daten. Neben dem Modifizieren von Daten für die Weitergabe an andere Layers hat das Presentation Layer keine weiteren Aufgaben.

### Application Layer (7)

Das Applikation Layer ist das Layer, mit dem der User interagiert. Es kann zum Beispiel die Kommandozeile oder ein Menü sein. 

### Unterschied Transportation Layer und Session Layer

In essence, the Session Layer focuses on the management and coordination of the overall session, which may involve multiple interactions and transactions between two devices. It sets up and organizes the session but doesn't directly handle the transfer of data packets. Once the session is established, the Transport Layer takes over and ensures the reliable and orderly transfer of data between the two devices.

So, it's more accurate to say that the Session Layer manages the session's establishment and coordination, while the Transport Layer handles the actual data transfer and reliability once the connection or session is established.

(Von ChatGPT kopiert)

### Einfache Erklärung der 7 Layer

- 7-5 → Daten / Produkt zum Versand werden generiert
- 4    → Es wird in Kisten verpackt
- 3    → Ich schreibe die Adresse darauf
- 2    → Ich mache eine Inventarliste und lege sie bei
- 1    → Das Versenden per Post

### DoD / TCP / IP-Modell

- Gröbere Ansicht als OSI, meist ausreichend für reine Netzwerk-Probleme
- 4 Schichten:
    1. Anwendung
        1. Protokolle, die mit Programmen zusammenarbeiten und das Netz für den Austausch von Daten nutzen (zB. HTML, DNS, FTP)
    2. Transport
        1. Stellt die Ende-zu-Ende Verbindung her und generiert kleine Datenpakete, die in die unteren Schichten übermittelt werden (zB. TCP und UDP)
    3. Vermittlung
        1. Hier wird immer wieder das nächste Zwischenziel ermittelt und die Pakete dorthin weitergeleitet (Punkt-zu-Punk). Kern dieser Schicht ist das Internet Protocol (IP)
    4. Netzzugangsschicht
        1. Diese Schicht kümmert sich um die Übertragung von Daten auf verschiedene Medien (zB. Ethernet, PPP, IEEE 802.11)

# Lernziele

- Verständnis von
    - Netzen
    - Protokollen
    - Übertragungsmedien
    - Topologien
- Können selbstädnig mit Hilfe von einem Schichtenmodell einen Problemlösungsansatz definieren und umsetzen

# Kabel und Stecker

### Übertragungsmedien Drahtlos

- Bluetooth
    - Meist für PAN-LAN Netzwerke
    - Datenübertragung ist 3 Mbps
- WLAN
    - Datenraten bis 9607.8Mbps möglich

### Übertragungsmedien Drahtgebunden

- Twisted Pair Kabel
    - Besteht aus gewundenen Paaren von Drähten, die gemeinsam in einem Kabel stecken. Es gibt verschiedene Variationen:
        - CAT 1-4 → Wurde für Telefonleitungen verwendet, aber heutzutags nicht mehr anzutreffen
        - CAT5 → 100MBit
        - CAT6 → 1GBit
        - CAT7 → 10GBit
    - Bei Twisted Pair-Kabeln werden verschiedene Arten von Schutz verwendet.
        - UTP → Unshielded, kein Schutz
        - FTP → Foiled, mit Alufolie geschützt
        - STP → Shielded, mit Kupfergeflecht geschirmt
        - S/UTP → Adern ungeschrimt, Kabel geschirmt
        - S/STP → Adernpaar geschirmt, Kabel geschirmt
    - 100m Reichweite von Aktivem zu Aktivem Gerät
- Kupfer - Koax
    - Früher übliches Kabel, das heutzutags von Twisted Pair Cables abgelöst wurde.
- Fiber / Glasfaser
    - Glasfaser überträgt Lichtimpulse, keine elektronischen Signale
    - Datenraten bis 39 Tbit/s möglich
    - Glasfaster (auch LWL genannt) hat verschiede Anschlüsse:
        - OM1 / OM2: Standart bis 1GBit/s
        - OM3 / OM4: Für mehr Speed wie 10GBit/s

### Stecker

- RJ45
    - Stecker für 8-Adrige twisted-pair-cables
    - RJ steht für “Registered Jack”
- BNC
    - Stecker für Koax-Kabel
- Lichtwellenleiter / Glasfaser
    - Für Glasfaser gibt es einige verschiedene Stecker, die alle verschiedene  Anwendungsbereiche haben.

### Arten von Verkabelung

- Primäre verkabelung
    - Verkabelung zwischen Gebäuden
    - Gut für weite Strecken
    - Galvanische Trennung (kein Austausch von Strom möglich)
    - Meist Glasfaser
- Sekundäre Verkabelung (Vertikale Verkabelung)
    - Zb. innerhalb eines Gebäudes zwischen den Etagen
    - Sollte Glasfaser sein, wird aber auch mit Kupfer gemacht
- Tertiäre Verkabelung
    - Horizontale Verkabelung (direkt zu Computer)
    - Kupferverbindung