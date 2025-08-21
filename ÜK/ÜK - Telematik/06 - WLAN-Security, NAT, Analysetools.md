#ÜK
#telematik
# Wlan-Security

## Lernziele

- Über die Sicherheit im WLAN bescheid wissen
- Sie können Vorschläge zur Verbeserung der Sicherheit und der Geschwindigkeitsoptimierung machen
- Wissen, wo man Sicherheitseinstellungen vornehmen muss

## Wlan-Pros

- Keine Kabel
- Schnelle Entwicklung
- Einfache Gebietsabdeckung

## Wlan-Contras

- Abhören
- Sicherheit
- Geringe Qualität/Datenverkehrskontrolle

## Arten von Security

### SSID

SSID steht für Service Set Identifier. Es ist der Name eines WLAN-Netzwerks.

### WEP/WPA/WPA2

WEP = Wired equivalent privacy | WPA = Wifi Protected Access

WEP war der erste Verschlüsselungsstandart im Wireless-Bereich, es ist mittlerweile nicht mehr sicher und durch neuere Methoden ersetzt worden. Es nutzt die Verschlüsselungsmethode RC4

WPA ist der aktuelle Standart für Netzwerke. Im Gegensatz zu WEP hat es Preshared Keys und Authservers

WPA-PSK ist der Pre-Shared Key des WPA-Standarts (Muss auf allen Knoten kofiguriert werden). Häufig wird dieser jedoch zu selten gewechselt und/oder ist zu einfach.

WPA-EAP steht für Extensible Authentication Protocol, es nutzt Username und Passwort anstatt einen statischen Schlüssel.

WPA2 nutzt AES-Verschlüsselung anstatt RC4, welches von WEP verwendet wird. 

WPA3 ersetzt den PSK mit SAE (Simultaneous Authentication of Equals)

### RC4/AES

RC4 ist die Verschlüsselung, welche von WEP verwendet wird.

### PSK/AES

PSK steht für Pre-Shared-Key, welcher wie ein Passwort fungiert.

### MAC-Filter

Filtert, welche mac-Adressen durchgelassen werden

## Prävention von Sicherheitslücken

In grossen Firmen wird Sicherheitssoftware angewendet, die das Netzwerk nach Schwachstellen scannt und diese in einem Bericht zusammenfasst.

Eine weitere Sicherheitsmassnahme sind Logs, die sämtliche Zugriffe speichern und auswerten. Diese Logs muss man natürlich regelmässig anschauen und besprechen.

## Liste von Sicherheitsmassnahmen

- Standart-Passwort ändern
- SSID ändern (kein Firmenname oder Hersteller)
- WPA2 oder etwas neueres verwenden
- Keine Fernkonfiguration erlauben
- Access Point ausschalten, wenn nicht verwendet
- Reichweite des WLANs einschränken
- Regelmässig Updaten und regelmässig Logs auswerten

# NAT

### Lernziel

Lernende wissen, was NAT ist und wie es eingesetzt wird

NAT steht für Network Adress Translation. Es wird gebraucht, da es zu wenige IPv4-Adressen gibt, um allen Devices eine zu geben. Es erlaubt mehreren Geräten, die sich in einem privaten Netzwerk befinden, sich eine einzige öffentliche IP zu teilen. NAT ändert die Quell-IP von versendeten Packeten zu der öffentlichen des Netzwerks. Durch das verstecken von Quelladressen ist es ausserdem schwieriger, einen Angriff auf die Infrastruktur durchzuführen.

Der Router, welcher die Umrechnung von privater zu öffentlicher IP vornimmt, speichert die Umschreibung in einer Tabelle ab. Wenn eine Antwort zurück kommt, kann er anhand der Tabelle entscheiden, zu wem (welcher IP) die Daten gesendet werden müssen.

Bei IPv6 wird kein NAT verwendet, da es genug mögliche Adressen gibt um jedem Gerät eine individuelle zu verteilen.

### Beispiel

Ein Client sendet eine Anfrage an einen Server. Da Server und Client aber in unterschiedlichen Netzen sind, ändert der Router die Quell-IP zu seiner eigenen, bevor der die Anfrage an den Server weiterleitet. Der Router speichert ausserdem die Änderung der Quell-IP in seiner Tabelle ab. Wenn der Server antwortet, sendet er die Antwort an den Router, welcher anhand seiner Tabelle weis, an welches Gerät er diese weiterleiten soll.

Weder Client noch Server bemerken etwas vom austausch der Quell-IP!!!

# Analysetools

## Lernziele

- Die gängigen Netztools kennen und einsetzen können
- In der Lage sein, Netzprobleme systematisch zu analysieren

## Die Tools

### Netzzugangsschicht

Analyse des Netzzugangs wird mit `arp`(Adress Resolution Protocol) gemacht. Diesen Befehl kann man in die Windows-Cmd eingeben und zeigt an, welche Adressen im Netzwerk verwendet werden.

### Vermittlungsschicht

Mit `ipconfig`kann man sehen, was die  eigene IP und Subnetmaske ist. `ipconfig /all` gibt einem auch noch Informationen über DHCP-Protokoll und weitere. Wichtig sind `/all`, `/release`, welcher die zugeteilte IP wieder freigibt und `/renew`, welcher nach dem release eine neue IP anfordert.

Der `ping`-Befehl lässt einen die Verbindung testen. Mit `ping -a` löst es auch den Namen auf (zeigt diesen an). So bekommt man einen Eindruck davon, ob die gewünschten Adressen erreichbar sind.

Mit `routeprint` kann man die Routentabellen sehen.m

### Transportschicht

Auf der Transportschicht befinden sich alle Ports und Sockets. Mit `netstat -an` kann man die offenen Netzverbindungen anschauen. Mit `telnet <ip> <socketnummer>` kann man einzelne Sockets testen und mit `nmap` Sockets systematisch nach offenen Ports scannen.

Für telnet im CMD das eingeben zum installieren:

**dism /online /Enable-Feature /FeatureName:TelnetClient**

### Anwendungsschicht

`nslookup <ip>` lässt einen Anfragen, welcher Hostname zur IP gehört. 

Wireshark ist ein Tool, das einem noch eine genauere Analyse erlaubt.