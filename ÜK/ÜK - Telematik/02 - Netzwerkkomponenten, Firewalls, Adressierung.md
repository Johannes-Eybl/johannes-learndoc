#ÜK
#telematik
# Netzkomponenten 1&2

## Layer 1

### Netzwerkkarte / NIC → Layer 1+2

NIC steht für Network Interface Card/Connector. Man darf die NIC aber nicht mit physischen Ports verwechseln. Die NIC ist praktisch nur ein Chip, der Daten verarbeitet. Mehrere Ports können sich einen Chip teilen! 

### Amplifier & Repeater → Layer 1 + 2

### Amplifier

- Verstärkt das elektronische Signal, kann aber keine Fehler beheben und leitet diese einfach weiter.

### Repeater

- Regeneriert das elektronische Signal. Manche Repeater haben Zugriff auf höhere Layers und können darum fehlerhafte Signale reparieren.
- Repeater eliminieren Noise aus dem Signal, bevor es verstärkt wird.
- Ein Repeater wandelt Signale, die nicht präzise auf 1 oder 0 sind, zum passenden Wert um. Beispiel: Über eine Distanz hinweg wird eine 1 zu einer 0.8. Diese 0.8 wird vom Repeater wieder zu einer 1 gemacht - es wird Regeneriert.
    
    Im unteren Bild sieht man, wie ein Abnormales Signal aussehen würde.
    
    ![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%205.png)
    

Praktisch werden heutzutags in den meisten Fällen Repeater verwendet. Amplifier werden vor allem gebraucht, um ein Signal über grosse Distanzen leiten zu können. Da Repeater das Signal aber nicht nur verstärken, sondern auch die Qualität des Signals verbessern, sind sie beliebter.

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%201%202.png)

## Layer 2

### Switch → Layer 2

- Verbindet Geräte im gleichen Netz, entscheided zu welcher Adresse ein Datenpaket gesendet werden muss
- Lässt einen mehrere RJ45-Stecker anstecken, dadurch kann man viele Geräte Physisch verbinden
- Merkt sich, welche MAC-Adresse an welchem Port angeschlossen ist und sendet Daten nur an die richtigen MAC-Adressen. Dazu wird ein “MAC adress table” verwendet.

Es gibt auch Layer 3 Switches, also Switches, die routen können und Router die switchen können.

### Bridge → Layer 2

Eine Bridge ist dazu da, mehrere Geräte oder mehrere Netze zu verbinden und den Datenverkehr zwischen diesen zu kontrollieren. Genau wie ein Switch muss sie entscheiden, welche Datenpakete zu welcher Adresse gesendet werden. 

Bridges werden teils auch als Repeater verwendet, um ein Signal über längere Distanzen übertragen zu können. 

Bridges sind häufig dazu fähig, von einem Übertragungsmedium zu einem anderen zu wechseln. ZB. Glasfaser zu Kupfer oder Kupfer zu Wlan

### Unterschied Switch und Bridge

Aus technischer sicht besteht kein grosser Unterschied zwischen Switches und Bridges. Meistens haben Bridges viel weniger Anschlüsse als Switches. Das bedeutet, dass Switches praktisch viel häufiger genutzt werden, da sie flexiebler sind. 

## Layer 3

### Router → Layer 3

Ein Router ist u.a. dafür verantwortlich, den Weg zu wählen, über den die Daten versendet werden. Das macht er mithilfe von Gewichtung, Protokollen und MAC-Adressen.

Die zweite wichtige Aufgabe des Routers ist die Vorbereitung der Daten, damit diese bereit dazu sind, versendet zu werden.

- Verbindet verschiedene Netze miteinander, hat daher min. zwei Ports.
- Ist immer die äusserste Grenze des Netzes (verbindet das lokale Netz mit äusseren Netzen)
- Kann, aber muss nicht ein Gateway sein. Ein Gateway kann auch auf anderen Layers sein.

# Firewalls

In der Default-Konfiguration wird meistens zwischen *Default Block* und *Default Allow*  unterschieden. Das bedeutet, dass entweder alles geblockt oder alles durchgelassen wird. Anschliessend kann man entscheiden, welche Sachen man öffnen oder schliessen will.

Da Firewalls häufig ein Bottleneck des Netzwerkes sein können, ist es wichtig, diese überdimensioniert zu planen.

### Firewall (Hardware) → Layer 1-4

- Ist physisch und mindestens an zwei Netze angeschlossen
- Konfiguration gibt vor, was rein- oder rausgelassen wird zb. LAN→WLAN oder umgekehrt
- Konfiguriert wird eine Firewall über ein Webinterface

### Firewall (Software) → Layer 5-7

- Ist eine Software auf einem Host und gibt vor, was von dem Host an das Netz rein / raus gelassen wird
- Manche Betriebssysteme haben eine eingebaute Firewall, zB. die Windows Defender Firewall
- Eine Software-Firewall ist *nicht* dasselbe wie ein Content-Filter!

# Adressierung

Lernziel → Die Lernenden können auswendig zwei Arten der Adressierung benennen.

## MAC - Media Access Control

Jedes Gerät (präzise gesagt jeder Adapter), welches mit/in einem Netzwerk kommuniziert, hat eine MAC-Adresse. Bsp: UE-Boom, Handys, Computer. Die MAC-Adresse eines Geräts ist nicht veränderbar, da direkt an die Hardware gekoppelt.

### Aufbau MAC-Adresse

Jede MAC-Adresse besteht aus 6 Hex-Zahlen bzw. aus 48 bits. Die erste Hälfte der Adresse ist herstellerspezifisch (OUI - Organizationally Unique Identifier) und die zweite Hälfte wird vom hersteller vergeben (ist also für das Gerät selbst). Beispiel einer MAC-Adresse;

5C-F9-C8-05-DD-1A

## IPv4

- Jede IPv4-Adresse hat vier Zahlen, die zwischen 0 und 255 liegen
    - Beispiel: 192.168.1.25
- Technisch gesehen ist es eine 32-Stellige Binärzahl
- Private IPs haben folgende Zahlen am Anfang:
    - 192.168.x.x
    - 172.16.x.x bis 172.31.x.x
    - 10.x.x.x
    - 169.254.x.x

## IPv6

IPv6 wurde eingeführt, um mehr mögliche Adressen zu haben, da IPv4 zu knapp wurde. Aufgeteilt wird die IPv6-Adresse in 8 Blöcke à 16 bits. Das sieht folgendermassen aus:

2a00:1450:400a:0802:0000:0000:0000:200e

IPv6-Adressen werden immer in Hexadezimal geschrieben, jede Stelle kann zwischen 0000 und FFFF sein (In dezimal geschrieben zwischen 0 und 65’536)