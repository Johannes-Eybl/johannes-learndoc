#ÜK
#telematik
# DHCP (Dynamic Host Configuration Protocol)

## Lernziele

- Wissen, was DHCP ist
    - DHCP ist ein Protokoll, mit dem Server IP Adressen managen können und diese an Clients verteilen. Wenn sich ein Gerät in ein Netzwerk mit DHCP anmeldet, bekommt es vom DHCP-Server eine IP und Subnetzmaske zugeteilt. Ausserdem kommt diese zugeteilte Adresse mit einem Lease, der festlegt wie lange der Client die Adresse behalten kann.
- Wissen, weshalb DHCP eingesetzt wird
    - Ohne DHCP müsste man bei einem Netzwerk (vorallem bei grösseren) ständig manuell IP-Adressen verteilen. Immer, wenn ein Gerät dem Netzwerk beitreten will, braucht es eine IP-Adresse. Bei manueller Verteilung hätten Geräte ausserdem immer die selbe IP, was zu erhöhten Sicherheitsrisiken führt.
- Wissen, wie man IP-Konfigurationen beim Client prüft
    - Auf Windows kann man mit `ipconfig` bzw. `ipconfig /all` u.a. die IPv4 und IPv6 Adressen des Computers sehen.

## Protokollablauf

1. DHCP-Discover → Wenn sich der Client mit dem Netz verbindet, sendet er eine Broadcast-Message, um den DHCP-Server des Netzwerks zu finden.
2. Wenn der Server die Message erhält, antwortet er mit einer verfügbaren IP-Adresse und weiteren optionalen Informationen (zB. DNS-Server-Adressen oder Gateway-Adressen)
3. Der Client antwortet mit einer Anfrage für die IP-Adresse, die ihm zuvor gesendet wurde. (”*Ja, ich will diese IP-Konfiguration*”)
4. Der Server antwortet mit einer Anerkennung (Acknowledgement) der IP-Anfrage und beendet damit den Ablauf des Protokolls. 

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%209.png)

![Untitled](Untitled%201%206.png)

![Untitled](Untitled%202%202.png)

# Routing

[https://www.youtube.com/watch?v=VW6rnNj0pPU](https://www.youtube.com/watch?v=VW6rnNj0pPU)

## Lernziele

- Den Zweck des Routings erklären können
- Die verschiedenen Arten von Routing kennen
- Wissen, dass es Routing-Protokolle gibt
- Erklären können, was die default Route ist

## Begriffe

- Destination → Ziel, Netz-ID
- Gateway → Next Hop, nächster Schritt
- Netmask → Netzmaske, CIDR
- Metric (!) → Gewichtung, wenn mehrere Routen möglich sind hilft diese dem Router, eine Entscheidung zu treffen, welche Route zu bevorzugen ist. Kann statisch eingesetzt werden. Wenn dynamisch etabliert, wird diese Aufgrund einer Reihe von Informationen berechnet (Path lenght, bandwidth, load, hop count, maximum transmission unit etc.)

Ein Router entscheidet, wohin ein Paket weitergeleitet wird, damit es ans Ziel kommt.    Befinden tut sich der Router auf dem dritten OSI-Layer. Um eine Route zu berechnen, verwendet der Router eine Routing-Tabelle

## Statisches Routing

Wenn man statisch routet, muss man selber eine Routing-Tabelle schreiben und entscheiden, welche Pfade und Routen sinnvoll sind.

### Vorteile

- Einfach
- Volle Kontrolle
- Kein Overload im Netz, also kein Datenverkehr welcher nicht vom User verursacht wurde

### Nachteile

- Jede Änderung muss manuell eingegeben werden
- Keine Fehlertoleranz, schon kleine Ungenauigkeiten können das Netz lahmlegen
- Je grösser das Netz, um so anstrengender der manuelle Aufbau

## Dynamisches Routing

Bei dynamischem Routing baut der Computer anhand eines Routing-Protokolls selber eine Tabelle auf, legt also selbstständig Pfade und Routen an (es gibt mehrere Algorithmen, die Routen berechnen können).

### Vorteile

- Einfache Konfiguration
- Fehlertoleranz
- Möglichkeit für Loadbalancing

### Nachteile

- Netzwerkbelastung (es gibt viel administrativen Traffic)
- Ressourcenbelastung auf dem Router
- Routenwahl wird von Router entschieden, man hat nur relativ kleinen Einfluss

## Routing Tables

Routing-Tabellen werden dazu verwendet, Routen zu berechnen. Beispiel Routing-Table:

![0.0.0.0 ist der Default-Gateway, welcher genutzt wird um zu anderen Netzwerken zu verbinden.](Untitled%203%202.png)

0.0.0.0 ist der Default-Gateway, welcher genutzt wird um zu anderen Netzwerken zu verbinden.

- Destination → Die IP-Adresse des Zielnetzwerks
- Netmask → Die Klasse / Range des Zieladresse, wird benutzt um das Subnetz der Zieladresse zu berechnen
- Gateway → Die nächste IP-Adresse, zu der die Daten weitergeleitet werden.
- Interface → Das ausgehende Interface (Netzwerkkarte), durch das die Daten gesendet werden sollen.
- Metric → Die Metric gibt jeder Route einen Wert und kann beispielsweise die Anzahl von Sprüngen angeben. Der Router wählt dann anhang von der Metric die geeignete Route.

# WLAN-Grundlagen

## Lernziele

- Arten der drahtlosen Kommunikation kennen
    - RFID, Bluetooth, Leuchtturm, Infrarot, WIFI, Mobiltelefon
- Strahlenproblematik verstehen
    - Die Strahlenproblematik besagt, dass wenn zu viele Signale auf den gleichen Frequenzen sind, die einzelnen Signale sehr schwach werden bzw. nicht mehr unterscheidbar sind.
- Die WLAN-Standarts und deren Unterschiede kennen
    
    ![Brutto → Theoretische Maximal-Werte | Netto → optimaler realer Durchsatz für ein Gerät](Untitled%204%201.png)
    
    Brutto → Theoretische Maximal-Werte | Netto → optimaler realer Durchsatz für ein Gerät
    
- Den neusten Standart im WLAN-Bereich kennen
    - Der aktuelle Stand vom Wifi ist 802.11ac und .11ax
    - Ganz neu ist .11ad, was jedoch nicht genutzt werden kann

## Drahtlose Kommunikation

Ein Gerät, welches ein WLAN-Signal aufnimmt und dieses auf einem Kabel weiter gibt, ist eine Bridge. Bridges werden allgemein dazu verwendet, um von einem Übertragungsmedium zum anderen zu wechseln.

## Betriebsarten

### Ad-Hoc-Modus

- Alle Stationen gleichwertig
- Jeder kann mit jedem kommunizieren

### Infrastruktur-Modus

- Basisstation (meist Access Point) wird speziell gehandhabt
- Kommunikation läuft meist über AP