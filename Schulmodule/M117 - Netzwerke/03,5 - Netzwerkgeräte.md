#schule 
#m117

# Ziele

- Den Unterschied zwischen aktiven und passiven Netzwerkgeräten kennen
    - Manche Netzwerkgeräte brauchen keine Stromzufur und sind dadurch passive Geräte
- Die Unterschiede in der Funktionsweise der aktiven Netzwerkkomponenten erklären
- Die gängigen Szenarien für Netztrennung mittels Firewall-Routern aufzeigen
- Aufgaben und Einsatzzweck unterschiedlicher Netzwerkgeräte nennen
- Den Einsatz von Netzwerkgeräten in einem Netzwerk planen und die Geräte konfigurieren

# Übersicht Netzwerkgeräte

![Untitled](Schulmodule/M117%20-%20Netzwerke/Fotos%20&%20PDFs/Untitled%204.png)

## Netzwerkkarte

Netzwerkkarten lassen die Verbindung von PCs und RJ45-Steckern zu. Meistens in den PCi-Slot eingesteckt werden sie für die erweiterung der Netzwerkmöglichkeiten verwendet.

## Repeater

Ein Repeater verstärkt ein Signal, sodass man dieses über längere Distanzen übertragen kann.

## Hub (Multiport-Repeater)

Ein Hub verbindet mehrere Geräte miteinander, doch es können alle übertragenen Daten von allen angeschlossenen Geräten gelesen werden.

## Switch

Switches verbinden mehrere Geräte bzw. mehrere Netzwerke mit einander. Im Gegensatz zu Hubs sind die übertragenen Daten von einander getrennt und können nicht von allen Geräten gelesen werden. Switches sind das meist benutzte Gerät bei der Netzwerktechnik.

## Router

Router können verschiedene Netzwerke mit verschiedenen IPs mit einander verbinden. Sie Routen die Daten, welche vom WAN ankommen. Das bedeutet, sie entscheiden, wohin empfangene Daten weiter geleitet werden müssen. 

## Media-Converter (Bridge)

Converter sind Brücken zwischen verschiedenen Übertragungsmedien, zb Kupfer zu Glas.

## Modems

Modems sind veralterte Dinger, die ein Gerät via Telefonleitung mit Internet verbunden haben.

## Firewall

Firewalls filtern den Internetverkehr, blockieren also bestimmte IPs und shady stuff.

### Bastion Host Firewall

Die meisten Haushalte haben eine Firewall, die den gesamten Haushalt vor dem “bösen Internet” schützt. 

![Untitled](Schulmodule/M117%20-%20Netzwerke/Fotos%20&%20PDFs/Untitled%201%202.png)

### Three Homed Firewall

Manche Firewalls teilen das LAN in zwei Teile auf. Ein Teil ist vor dem Internet geschützt und ein anderer Teil ist offen, sodass er via Internet erreichbar bleibt. Ein Beispiel für den praktischen Nutzen dieses Aufbaus sind Firmen, welche einen Öffentlichen Server haben, der erreichbar sein muss.

![Untitled](Schulmodule/M117%20-%20Netzwerke/Fotos%20&%20PDFs/Untitled%202%201.png)

### Screened Subnet

Dieses Setup benutzt den öffentlichen Teil des Bastion Host Setups als zwischenschritt für den Zugriff aufs private Lan. 

![Untitled](Schulmodule/M117%20-%20Netzwerke/Fotos%20&%20PDFs/Untitled%203%201.png)