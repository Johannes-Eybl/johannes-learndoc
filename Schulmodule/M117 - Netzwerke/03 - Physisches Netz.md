#schule 
#m117
[Präsentation 117_2 Netzwerkgrundlagen.pdf](Prsentation_117_2_Netzwerkgrundlagen.pdf)

[Präsentation 117_3_1 Physisches Netz - Medien und Verkabelung.pdf](Prsentation_117_3_1_Physisches_Netz_-_Medien_und_Verkabelung.pdf)

### Auftrag Übertragungsmedien

Vor- und Nachteile der verschiedenen Übertragungsmedien finden

| Medium | Internetzugang Vorteile | Internetzugang Nachteile | LAN Vorteile | LAN Vorteile |
| --- | --- | --- | --- | --- |
| Glasfaser | Schnell | Teuer | Teuer | Schnell |
| Kupferkabel | Billig | Schnell ausgelastet | Billig | Nicht für grosse Netzwerke nutzbar |
| Modilfunk / WLAN |  | Auf grösse Distanzen zu langsam | Unkompliziert, flexiebel |  |

# Ziele physisches Netz

- Ziele der strukturierten Verkabelung nennen
- Vor- und Nachteile sowie Einsatzzwecke unterschiedlicher Übertragungsmedien erklären
- Aufgaben und Einsatzzweck unterschiedlicher Netzwerkgeräte nennen
- Den Einsatz von Netzwerkgeräten in einem Netzwerk planen und konfigurieren

# Strukturierte Verkabelung

Die strukturierte Verkabelung ist ein Aufbauplan für das Netzwerk zwischen verschiedenen Diensten. Es wird in einen primären, sekondären und tertiären Bereich eingeteilt. 

## Warum man strukturierte Verkabelung macht:

- Unterstützung der heutigen und künftigen Kommunikationssysteme
- Reserve in Bezug auf die Übertragugskapazität
- Neutrales Verhalten gegenüber Übertragungsprotokoll und Endgeräten
- Einfache erweiterbarkeit
- Ausfallsicherheit durch sternenförmige Verkabelung

## Die drei Bereiche der strukturierten Verkabelung

Von dem MAN aus leitern Verteiler Daten an kleinere Netzwerke weiter. Diese Verteiler sind in mehreren Stufen angebracht und ergeben eine Sternförmige Netzwerkstruktur.

### Primärverkabelung (Geländeverkabelung)

Die Primär- oder Gebäudeverkabelung sieht, wie der Name sagt, die Verkabelung einzelner Gebäude untereinander vor. (Max Kabellänge 1500m)

### Sekundärverkabelung (Gebäudeverkabelung)

Diese Kategorie der Verkabelung dreht sich um das verkabeln von einzelnen Wohnungen oder Stockwerken in einem Gebäude untereinander und von/zu dem Teil des Netzwerks, welcher für die Primärverkabelung da ist. (Max Kabellänge 500m)

### Tertiärverkabelung (Etagenverkabelung)

Diese Kategorie der Verkabelung beschreibt die Verbindung von Etagen- oder Stockwerkverteilern zu Anschlussdosen (die Dose in der Wand oder Arbeitsplatz, welche der Nutzer verwendet). Dafür werden Twistet-Pair-Kabel verwendet, mit einer max. Länge von 90m. Das Kabel von Anschlussdose zu Engerät ist max. 5m

# Übertragungsmedien

## Kupfer

### Kabel

Bei Kupferverkabelungen werden meistens Twisted-Pair-Kabel eingesetzt. 

Diese Kabel sind in mehrere Kategorien eingeteilt, welche ihre Leistungsfähigkeit beschreiben.

![Untitled](Schulmodule/M117%20-%20Netzwerke/Fotos%20&%20PDFs/Untitled%201.png)

### Stecker

Typische Stecker für Kupferkabel sind RJ-45 Stecker, welche bei max. Cat6A eingesetzt werden können (bis max. 55m). Für höhere Cat-Stufen gibt es neuere Steckertypen wie GG45 oder Tera.

### Schirmung

So wie es Klassen für Leistung gibt, haben Kabel ebenfalls eine Kategorei für ihre Abschirmung. Diese Schirmung schützt vor elektromagnetischen Strahlen. Beispiel:

UUTP-Kabel steht für Ungeschirmt-Ungeschirmt-Twisted-Pair

SSTP-Kabel steht für Geflechtschirm-Geflechtschirm-Twisted-Pair

![Untitled](Schulmodule/M117%20-%20Netzwerke/Fotos%20&%20PDFs/Untitled%201%201.png)

## Glas

Glasfaserkabel waren früher einmal nur eine Zukunftsvorstellung, doch sind jetzt Realität. Es ist das ideale Übertragungsmedium für die schnelle Übertragung grosser Datenmengen.

### Vorteile

- Geringe Dämpfung und dadurch bessere Übertragung
- Licht kann mehrere Kilometer übertragen werden
- Beschädigungen sind leicht zu finden
- Immun gegen elektromagnetische Störungen
- Glasfaserkabel können grössere Datenmengen transportieren als Kupferleitungen

### Nachteile

- Glasfaser ist teurer als andere Übertragungsmöglichkeiten
- Glasfaser ist anfällig gegenüber mechanischer Belastung (Druck, Verbiegung, Staub oder Wasser)
- Über Glas kann kein Strom übertragen werden

### Arten von Faserkabeln

Es gibt mehrere Arten von Fasern, (Multimodefaser, Monomodefaser). Multimodefaser erlaubt es mehreren Photonen, gleichzeitig durch das Kabel zu reisen. Das kann bei grossen Kabellängen zu Problemen führen. Monomodefaser erlaubt es nur einzelnen Photonen durch das Kabel zu reisen, was eine höhere Übertragungsrate erlaubt. Ausserdem ist so eine höhere Übertragungsdistanz möglich. Dafür ist der Preis auch höher.

Bei der GIBB ist die Sekundäranschliessung via Multimode-Glasfaser realisiert.

### Stecker

Die häufigsten Steckerarten sind die LC- und SC-Stecker. LC für Swiches und Router, SC für LWL-Patchpanels.

## Luft

Es gibt eine Reihe von WLAN-Standarts, welche seit 1997 entstanden sind. 

![Untitled](Schulmodule/M117%20-%20Netzwerke/Fotos%20&%20PDFs/Untitled%202.png)

Diese Standarts haben maximale Übertragungsgeschwindigkeiten, welche auf der oberen Grafik im Bestfall möglich sind. Im Realfall gibt es jedoch meistens zu viele Störfaktoren, welche die Geschwindigkeit beeinträchtigen.

### Frequenzbereiche

Für WLAN gibt es zwei Frequenzbereiche - 2.4 und 5 GHz. Wichtig ist nicht nur Reichweite und Geschwindigkeit (5GHz hat mehr Gesch. aber weniger Reichweite als 2.4), sondern auch der Fakt, dass viele andere Geräte 2.4GHz brauchen und 5GHz eine “freiere” Frequenz ist.