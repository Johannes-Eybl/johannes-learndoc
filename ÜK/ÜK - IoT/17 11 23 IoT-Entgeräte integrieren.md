#ÜK
#IoT

# Datenverarbeitung - IoE-Endgeräte integrieren

## Ziele

- Du kennst drei Schichten der Datenverarbeitung im IoE auswendig
- Du kennst min. zwei Vor- und Nachteile der lokalen Datenverarbeitung und der Datenverarbeitung in der Cloud

## Im IoT gibt es drei Hauptlayers

- Sensing Layer *(Daten messen, Sensoren)*
- Networking Layer *(Datenübertragung von Sensing zu Processing Layer)*
- Processing Layer / Fog Layer *(Verarbeitung der Rohdaten)*
- Application Layer *(Zusammenführen der Daten, Aktionen definieren, Darstellung für Benutzer)*

## Processing Layer lokal oder in der Cloud

Wenn kein Internet vorhanden ist, kann der Cloud-Service nicht angesprochen werden. Darum will man bei kritischen Sicherheitskomponenten alles lokal machen. Ein gutes Beispiel dafür ist ein Ampelsystem, das auch bei Internetausfall funktionieren muss. Zugleich sollen zb. Rettungsdienste in der Lage sein, diese Ampel bei Notfällen bedienen zu können.

Ebenfalls relevant ist die Datensicherung, welche in der Cloud nicht garantiert werden kann. Eine Garantie kann man auch in einem lokalen Netzwerk keine machen, doch die Sicherheit ist zumindest deutlich grösser.

### Wann macht Lokal sinn

- Vollständige Datenhoheit
- Zusätzliche Infrastruktur benötigt

### Wann macht Cloud sinn

- Vorhandene Infrastuktur
- Integriert sich in bestehende Netzwerke

# Inbetriebsnahme

## Ziele

- Du benennst min. drei wichtige Schritte bei der Inbetriebahme von IoT-Gerääten
- Du kannst begründen, warum die Planung bei der Inbetriebnahme wichtig ist.
- Du weisst, warum IoT-Geräte in ein seperates Natzerwek plaziert werden

## Gefahren bei der Inbetriebnahme von IoT-Geräten

- Schlechte Planung
- Veraltete bzw. unsichere Firmware / Software
- Verschiedene Arten von Verbindungen
- Unklare Kommunikation mit Herstellerservern
- Schwache Passwörter / Verschlüsselung

# Datenschutz - IoE Endgeräte Integrieren

## Ziele

- Du nennst auswendig den Unterschied zwischen Datensicherheit und Datenschutz
- Du kannst min. 3 Arten besonders schützenswerter Personendaten auswendig aufzählen

## Wozu Datenschutz

- Schutz der Menschen vor der unberechtigten Nutzung ihrer Daten
- Begleitet den Prozess der Datenverarbeitung von Anfang bis Ende

## Unterschied Datensicherheit und Datenschutz

- Datensicherheit ist der technische Schutz vor (Daten-)Diebstahl oder Manipulation durch unberechtigte
    - Authentifizierung
    - Verschlüsselung
    - Backup
    - Physischer Schutz
- Datenschutz dreht sich um den Schutz der Persönlichkeitsrechten (informelles Selbstbestimmungsrecht). Es geht darum, welche Informationen an die Öffentlichkeit dürfen.

## Schützenswerte Personendaten

- Gesundheitsdaten
- Politische Ansichten
- Religion
- Finanzielle Situation
- Behördenkontakt (zB. Strafverfolgung)
- Bilder oder Biometrische Daten, welcher zu eindeutigen Identifizierung der Person beitragen