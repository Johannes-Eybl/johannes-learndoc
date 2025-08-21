#ÜK
#IoT

# Einführung M5Stack

## Lernziele

- Du kennst die wichtigsten Komponenten eines Raspberry Pi
- Du kennst die wichtigsten Komponenten eines M5Stack Core
- Du kennst den Entwicklungsprozess von UI FLow

## M5Stack Hardware

Die Basis des M5Stack ist der ESP32-Chip! Wenn man will, kann man Arduino damit verwenden.

Das Programmieren auf dem M5Stack funktioniert mit visuellem Programmieren, welches von der Maschiene zu Python übersetzt wird, das dann auf dem ESP32 läuft.

Für den M5 Gibt es duzende  Module, so wie auch Bases, welche die Funktionalität erweitern.

Der Bildschrim hat 320x240p!

![Untitled](ÜK/ÜK%20-%20IoT/Fotos%20&%20PDFs/Untitled%202.png)

- I2C Connector
- Gyroscope
- Wifi, Bluetooth
- GPIO Connector
- SD Card Reader
- Buttons
- Microphone
- RGB Lights
- Speaker
- Rechargeable Battery
- Display
- UART Connector

## Raspberry PI

Der Pi ist ein Mini-Computer auf ARM Basis, der mit Linux betrieben wird. Es gibt GPIO, was viele Anschlüsse ermöglicht. 

## Vergleich RaspberryPi / M5Stack

![Untitled](ÜK/ÜK%20-%20IoT/Fotos%20&%20PDFs/Untitled%201%201.png)

# Protokolle im IoE

## Ziele

- Du nennst min. drei häufig verwendete Protokolle bei IoE-Lösungenm
- Du kennst min. zwei Protokolle, welche beim M5Stack zur Anwendung kommen

Bei Ioe unterscheidet man zwischen internen und externen Protokollen

## M5Stack interne Protokolle

Folgende Protokolle werden von M5 unterstützt

- UART (Universal Asynchronous Reciever-Transmitter)
- I2C (Inter-Integrated Circuit)
- I/O (Entspricht GPIO)

## M5Stack externe Protokolle

Der M5 lässt sich auf folgende Arten mit externen Geräten verbinden:

- Bluetooth
- Wifi
- LoraWAN
- Ethernet

Mit diesen Verbindungen kann man HTTPS, MQTT und ESP-NOW verwenden.

Weitere Protokolle sind RFID, NFC, Z-Wave, Zigbee, LTE/4G/5G und SPI.

# Netzwerkbasierte Protokolle im IoE

## Ziele

- Du kennst min. zwei häufig verwendete Netzwerkprotokolle beo IoE-Lösungen
- Du kannst im Zusammenhang mit dem Protokoll MQTT den Begriff “Topic” erklären

## HTTP

HTTP ist ein TCP-basiertes Client/Server-Protokoll (Request-Response), welches vor allem im WWW verwendet wird. Es ist ein Unicast,  also ermöglicht es die Kommunikation zwischen einem einzelnen Sender und einem einzelnen Empfänger im Netzwerk.

## DDS

DDS (Data Distribution Service for Real-Time-Systems) ist ein spezifisch für IoT entwickeltes Protokoll, welches der aktuelle Standart für IoT-Geräte ist. Es ist ähnlich wie MQTT (publish/subscribe-Prinzip), doch etwas komplexer da umfangreicher. 

## MQTT

MQTT (Message Queue Telemetry Transport) ist ein für IoT entwickeltes, TCP basiertes Protokoll, welches für kleine Datenmengen optimiert ist. Es nutzt das “Publish/Subscribe”-Prinzip, was bedeutet, dass ein “Ding” Daten an einen Broker veröffentlicht und andere “Dinger” diese Daten vom Broker abholen können, wenn sie subscribed haben.

Der Broker leitet Daten von und zu Clients, der Publisher sendet Daten und der Subscriber empfängt Daten. Ein Gerät kann natürlich gleichzeitig beide Rollen erfüllen. 

### Beispiele

![Untitled](ÜK/ÜK%20-%20IoT/Fotos%20&%20PDFs/Untitled%202%201.png)

![Untitled](ÜK/ÜK%20-%20IoT/Fotos%20&%20PDFs/Untitled%203.png)

### Datenverwaltung (Topics&Subtopics)

Beim MQTT-Protokoll werden Daten mit Topics und Subtopics organisiert. Wie beim Windows-Dateissystem werden diese Topics mit “/” getrennt. 

- beispiel/eins
- beispiel/wetter/temperatur
- beispiel/wetter/luftfeuchtigkeit

Mit “/#” kann man sich auf alle Subtopics von dem Topic vor dem Strich beziehen.

Mit “/+/xyz” kann man sich auf alle Subtopics namens “xyz” beziehen, egal in welchem oberliegenden Topic sie drinnen sind. So kann man beispielsweise allen “Temperatur”-Topics eines Smarthomes subscriben.

### Spezielle Topics

![Untitled](ÜK/ÜK%20-%20IoT/Fotos%20&%20PDFs/Untitled%204.png)

### Adressierung bei MQTT

Alle Teilnehmenden in der MQTT-Kommunikation besitzen eine IP-Adresse. Optional brauchen Clients einen Benutzernamen und ein Passwort, um sich mit dem Broker verbinden zu können. Subscriber und Publisher können nicht direkt mit anderen Clients kommunizieren, nur Kommunikation mit dem Broker ist möglich.

Anwendungsbereiche von MQTT sind Sensoren&Sensordaten, Smarthomes oder Industrielle Steuerungen.

### Vorteile

- Einfach zu entwickeln
- Unbegrenzte Teilnehmerzahl
- Ressourcenschonend
- In vielen Programmiersprachen machbar
- Subscriber und Publisher müssen sich nicht kennen

### Nachteile

- Keine direkte Kommunikation
- TCP/IP Anbindung nötig
- Request&Antwort aufwändig

# Gerätenahe Protokolle

## Ziele

- Du nennst mind. zwei häufig verwendete gerätenahe Protokolle bei IoT-Geräten.
- Du weisst, wie bei RFID die Daten vom Transponder (Tag) zum Terminal gelangen
- Du benennst min. zwei der mitgelieferten externen Sensoren/Aktoren des M5-Stacks nach Protokoll (GPIO/I2C/UART)

## I2C

I2C wird bei der Kommunikation von Chips verwendet und wird beispielsweise in Datenwandlern (ADC), Anzeigeelementen oder in Speicherbausteinen verwendet. 

Das I2C-Protokoll basiert auf einer Single Primary, multi Secondary-Architektur. Das bedeutet, dass es einen Primary-Komponenten gibt, der die Kommunikation initiiert. Secondary-Komponenten kann es jedoch mehrere geben.

### Vorteile I2C

- Einfach aufgebautes Protokoll
- Wenig Hardware benötigt
- Mehrere Teilehmende möglich

### Nachteile I2C

- Kommunikation nur über kurze Strecken möglich
- Begrenzte Geschwindigkeit
- Primary muss Adressen&Aufbau aller Secondarys kennen
- Half Duplex - Bedeutet, dass die Informationen auf einem  Signalträger in beide Richtungen übertragen werden können.

## RFID

RFID steht für Radio Frequency Identification und ist ein Protokoll, das auf einem aktiven (mit Strom versorgten) und einem passiven Teil basiert. Es gibt dabei den Transponder (das Tag), welcher passiv ist, und das Terminal, welches Aktiv ist. Der Transponder bekommt die Energie durch ein elektromagnetisches Feld, worauf er seine gespeicherten Daten an das Terminal sendet. Dieses kann die Daten dann weiterverarbeiten.

Wichtig ist, dass die Daten nicht über die Spule gesendet werden, die die Energie überträgt. Stattdessen wird eine Antenne für die Datenübertragung verwendet.

![Untitled](ÜK/ÜK%20-%20IoT/Fotos%20&%20PDFs/Untitled%205.png)

Angewendet wird RFID bei Chips in Tieren, Fahrzeugidentifikation, Zahlungssystemen oder beim Diebstahlschutz.

### Vorteile

- Transponder braucht keine Energieversorgung
- Aufbau des Transponders ist cheap und einfach
- Transponder können eindeutig zugeordnet werden (Jedes Tag besitzt einen UUID - einen Universaly Unique Identifier)

### Nachteile

- Kommunikation nur über kurze Strecken, da passiver Transponder (<50cm)
- Nur wenige Daten können vom Transponder gespeichert werden (4 Byte bis 8 kByte)

## UART

Der Universal Asynchronous Receiver-Transmitter wird für einfache Device-To-Device Kommunikation verwendet. Es benötigt nur zwei Drähte für die Kommunikation und kann gleichzeitig Daten senden und empfangen.

## I/O

I/O ist eine generische Schnittstelle für Schaltkreise, ihre Funktionalität ist abhängig von dem Gerät wo sie vorkommt.