#ÜK
#telematik
# Adressierung IPv4 (Subnetting)

## CIDR - Classless Inter-Domain-Routing

Mit CIDR kann angegeben werden, welcher Teil einer IP-Adresse für das Netzwerk und welcher Teil der IP-Adresse für ein individuelles Gerät vorhanden ist. Das wird gemacht, da sich mehrere Adressen eines Netzwerks nur in den letzten paar Ziffern der IP-Adresse unterscheiden. 

Um die “individuellen”-Ziffern von den “netzwerk”-Ziffern zu unterscheiden, wird bei CIDR eine Zahl hinter der Adresse angegeben, die anzeigt wie viele Bits von ihr für das Netzwerk verwendet werden.

## Private Adressen Cheatsheet

![Untitled](ÜK/ÜK%20-%20Telematik/Fotos%20&%20PDFs/Untitled%206.png)

## Subnetting

Man kann ein Netzwerk in verschiedene Teilnetze aufteilen. Da es pro Netzwerk nur 255 Adressen gibt, müssen sich die Teilnetze diese 255 untereinander aufteilen. Jedes Teilnetz hat eine Netz-ID (die tiefstmögliche IP des Netzes) und eine Broadcast-IP (die höchstmögliche IP des Netzes).

### Berechnung von NID und Broadcastadresse

1. IP-Adresse in Binär schreiben
2. Subnetmaske in Binär schreiben
3. Logisch UND anwenden um den Netzteil zu bestimmen
    
    Also eine neue Adresse bestimmen, in dem man beide Adressen nimmt und bei der neuen überall dort eine 1 setzt, wo bei *beiden* Adressen auch ne 1 ist. Die neue Adresse ist die Netz-Adresse (NID - Network-ID)
    
4. Hostteil alle Bits auf 1 setzen, um Broadcastadresse zu bestimmen

### FLSM Subnetting (Fixed Lenght Subnet Mask)

![Untitled](Untitled%201%203.png)

### VLSM Subnetting (Variable Lenght Subnet Mask)

Das gibts, da ist die Maske nicht fix sondern variabel 😞

# Adressierung IPv6

IPv6 ist so etwas wie die neuere Version von IPv4. Dank längerer Adressen ist es möglich, mehr mögliche IPs zu haben, was das Problem von zu wenigen IPv4’s löst. IPv6 wird im Internet häufig verwendet, funktioniert aber nur wenn alle teilnehmenden Geräte die Technologie unterstützen. 

2a00:1450:400a:0802:0000:0000:0000:200e

IPv6 hat 8 Blöcke à 16 Bits, welche mit Doppelpünkten getrennt sind. Die validen Werte sind 0000-FFFF, werden obviously in Hex geschrieben. 

## Kürzung von IPv6

Da IPv6-Adressen sehr lange sind, kann man leere Stellen (nur nullen) mit einem Doppelpunkt abkürzen. Ausserdem kann man mehrere Nullen mit nur einer einzelnen Null abkürzen.

Die oben gezeigte IPv6-Adresse würde dann so aussehen:

2a00:1450:400a:0802::200e

Man darf eine Adresse aber nur ein mal Kürzen, da sonst nicht ersichtlich ist, welche und wie viele Stellen gekürzt worden sind. 

## Netzteil & Hostteil

Normalerweise sind bei IPv6 die ersten 64 Bits der Netzteil und die letzten 64 der Hostteil. Dabei wäre die Netzmaske eine “/64”. Es können jedoch auch die letzten 16 bits des Netzteils für eine Subnetz ID verwendet werden. Dann wären es eine “/48”-Netzmaske.

## Adresstypen

IPv6 hat nicht die gleichen Adresstypen wie IPv4.

### Unicast

- Für ein Interface
- 2000:: bis 3FFF::

### Multicast

- Für eine Gruppe von Interfaces, alle werden über diese Adresse erreicht
- FF00:: bis FFFF::

### Anycast

- Eine Gruppe von Interfaces, nur das erste bzw. am nächsten Interface wird über diese Adresse erreicht
- 2000:: bis 3FFF::