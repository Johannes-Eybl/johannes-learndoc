#schule 
#m114
# Lernziele

- Aufzeigen, dass jegliche Dateien lediglich einen Binärwert darstellen
- Erklären, warum es viele verschiedene Dateiarten braucht.
- Die wichtigsten Dateiarten nennen und den Anwendungen zuordnen
- Den Speicherdarf von Dateiarten abschätzen
- Kein Lernziel, aber zwischen Speichergrössen (MB→GB→TB) rechnen ist äuä wichtig!

Alle Daten, die von Nutzern oder Programmen generiert werden, sind schlussendlich als Binärwerte gespeichert. Das Dateiformat gibt an, welches Verschlüsselungsprotokoll verwendet wurde.

Dass Dateigrössen keine schöne Dezimalzahl sind, liegt daran, dass ihre Grösse in Binär gerechnet wird. 8x2^20 = 1024 Kilobyte oder 1 Megabyte

### Es werden zwischen folgenden Dateiarten unterschieden:

- Ausführbare Dateien → Anwendungen oder Dateien mit Befehlen (.exe, .bat, .php)
- Systemdateien → Dienen zur Konfiguration von Hard- und Software (conf-Files wie .bin, .ini, .sys)
- Bibliotheken → Enhalten Programmierwerkzeuge für Anwendungen (.cls, .dat, .dll)
- Nutzerdaten →  Vom Nutzer erstellte Dateien

# Textcodierung

Mit dem Aufkommen von Computern wurde es notwendig, Schreibmaschienenzeichen durch binäre Werte zu Codieren. 

## ASCII

ASCII ist einer der wichtigsten Codierungen. ASCII kann mit 7 Bits 128  verschiedene Schriftzeichen darstellen. Da diese erste Version nur im lateinisch geprägten Sprachraum funktionieren konnte, haben sich schnell weitere Versionen entwickelt. Diese Versionen nutzten das achte Bit für eigene Zeichen. Das grosse Problem war aber, dass verschiedene Länder und Firmen unterschiedliche Standarts entwickelt haben und dadurch Inkompatible Systeme enstanden.

## Unicode

Das Problem, welches mit ASCII entstand, wollte Unicode lösen. Das Ziel war, alle je verwendeten Zeichen in einem einzigen Code zu sammeln und zugänglich zu machen.