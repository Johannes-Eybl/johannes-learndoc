#ÜK
#IoT

# Big Data

Die Menge aller Daten, welche die Menschheit kreiert und verwaltet, steigt exponentiell an. 

Es gibt irrsinnig viele Geräte und Applikationen, die ständig neue Daten trainieren.

# Testing im IoE

## Ziele

- Min 3 wichtige Teilbereiche beim IoE Testing auswendig benennen
- Selbstständig Testfälle zu den wichtigsten Teilbereichen des IoE-Testing formulieren

Testen bedeutet, ein Programm/eine Schnittstelle/ein Gerät mit vorhandenen Vorgaben zu vergleichen. Es geht nicht darum, Fehlerfreiheit aufzuzeigen, viel wichtiger ist es, Fehler zu belegen.

## Begriffe

- Testobjekt → Das Ding, welches getestet wird
- Testspezifikation → Legt festm was das Objekt können muss und was nicht
- Testfall → Genaue Beschreibung wie das Testobjekt getestet wird
- Testplan → Enthält spezifische Testfälle und deren Reihenfolge fürs Testen eines Objekts
- Testprotokoll → Dokumentation der Resultate der Testfälle

## Testfall

- Anhand der Anforderungen muss man verschiedene Testfälle erstellen
- Man braucht eine genaue Beschreibung des Testobjekt und wie getestet wird
- Beschreibt Systemvorraussetzugen, welche während dem Test erfüllt sein müssen
- Detaillierte Auflistung der Schritte mit klar definierter Eingabe
- Erhaltenes Resultat wird dokumentiert und mit erwartetem Resultat verglichen
- Einmal ist keinmal, also muss man den gleichen Testfall min. zwei mal durchführen

## Testmethoden (Black/White/Gray Box)

### Black Box

- Das Innenleben des Testobjekts ist nicht bekannt
- Es ist nur bekannt, was der erwartete Output bei definiertem Input ist

Die Gefahl bei dieser Testmethode ist, dass wichtige Funktione oder Teile des Testobjekts vergessen werden.

### White Box

- Das Innenleben des Testobjekts ist bekannt
- Bei jedem Teilabschnitt der Funktionalität ist bekannt, wie genau es funktioniert

Die Gefahr bei dieser Testmethode ist, dass der Tester vergessen kann, manche Sachen zu testen, da sie ja “eh” bekannt sind. So können wichtige Teile des Codes/der Funktionalität übersehen werden.

### Grey Box

- Das Innenleben des Testobjekts ist auf Komponentenebene bekannt, die Komponenten selber sind aber Blackboxes
- Mischung aus Black- und Whiteboxtesting

## Testfelder

Geräte haben verschiedene Bereiche (Felder), die getestet werden können. Dazu gehören

- Sicherheit
- Geschwindigkeit
- Usability (Benutzerfreundlichkeit)
- Kompatibilität
- Zuverlässigkeit
- Skalierbarkeit
- Datenintegrität

## Testobjekte

Es gibt verschiedene Arten von Tests, die man bei einem Gerät durchführen kann.

- Funktionstest → Sind die erwarteten Funktionen vorhanden?
- Benutzbarkeitstest → Kann das Gerät im geforderten Rahmen benutzt werden?
- Sicherheitstest → Erfüllt das Testobjekt die sicherheitsspezifischen Anforderungen?
- Performancetest → Hat das Testobjekt die erwünschte Geschwindigkeit?
- Kompatibilitätstest → Ist das Testobjekt mit der vorhandenen Infrastruktur kompatibel?
- Servicetest → Funktioniert das Testobjekt mit einem dazugehörigen Dienst?
- Betriebstest/Systemtest → Verhält sich das Testobjekt im Zusammenspiel mit dem Gesamtsystem wie erwartet?

![Untitled](ÜK/ÜK%20-%20IoT/Fotos%20&%20PDFs/Untitled.png)

## Testobjekte

Es gibt vier Bereiche von Testobjekten

1. Sensoren und Aktoren (Messen und Ausführen)
2. Applikation (Verarbeitung und Steuerung)
3. Netzwerk (Übertragung)
4. Backend und Datacenter (Speicherung)

# Raspberry PI & TICK-Stack

## Ziele

- Du verstehst Einsatzzweck von Raspberry Pi und TICK-Stack

## InfluxDB

Influx ist eine Zeitreihendatenbank, welche beispielsweise für Sensorenwerte oder für Aktienkurse verwendet wird. Jeder Eintrag enthält einen Zeitstempel (1), ein Measurement (2), dein Tag (3) und einen Wert (4). Das könnte so aussehen: Zeit, Temperatur, location=Bern, 23.

## Telegraf

Telegraf schreibt erfasste Daten in InfluxDB. Telegraf basiert auf Plugins

## Chronograf

Chronograf ist eine Webbasierte Visualisierung der mit InfluxDB gespeicherten Daten. Es funktioniert mit der InfluxQL-Abfragesprache. Wichtige Features sind Alerts (meldung bei bestimmten wahrgenommenen Werten) und Dashboards (Aufteilung der gespeicherten Daten in sinnvoll unterteilte Bereiche). 

## Grafana

Grafana ist ein Konkurrent zu Chronograf. Sie stellt Daten verschiedenerr Datenquellen dar, hat so wie Chronograf auch Dashboards und Alerts. 

## Chronograf vs Grafana

![Untitled](ÜK/ÜK%20-%20IoT/Fotos%20&%20PDFs/Untitled%201.png)

## Kapacitor

Kapacitor erlaubt ein fortgeschrittenes Altert-Handling.