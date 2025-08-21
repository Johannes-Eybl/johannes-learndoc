#ÜK
#datenbanken
## Das Problem

Wenn eine Reihe von Befehlen durchgeführt werden und dann einer davon nicht funktioniert, sind Teile der Daten korrupt. Eine Transaktion führt mehrere Arbeitschritte zusammen und sorgt dafür, dass alle diese Schritte entweder gemeinsam ausgeführt werden oder nicht ausgeführt werden (alles oder nichts). 

Um in SQL Transaktionen vorzunehmen, muss man am Anfang des Befehls, den man auslösen will, `start transaction` und am Ende `commit / rollback` schreiben.

Mit dem `rollback`-Befehl wird die Datenbank auf den Stand zurückgesetzt, den sie beim `start transaction` hatte. Diese Befehle müssen nicht alle in der selben Datei sein!

## Autocommit

Autocommit ist ein per default aktivierter Modus, es wird also alles direkt in der Datenbank geschrieben / verändert. Deaktivieren tut man diesen Modus mit `set autocommit=0`, was aber bedeutet, dass man alle Änderungen mit `commit` bestätigen muss. Ein `start transaction` setzt den `autocommit` ausser Kraft, bis `commit / rollback` kommt.

# DB-Optimieren

## Ziele

- Die Lernenden wissen, welche Faktoren Einfluss auf die Performance von Datanbankabfragen haben
- Alle Lernenden wissen, wie dir auf dem Server gespeicherten Daten optimiert werden können
- Alle Lernenden können die Performance von SQL-Queries Statements mit Hilfe von Indizes verbessern

## Performance messen

Die Performance kann man in der MySQL-Workbench sehen, in dem man vor das Statement `explain` schreibt

## LIMIT

Mit dem LIMIT-Befehl kann man die Anzahl der ausgegebenen Zeilen angeben. Zb. tut `*mySQLquerie* LIMIT 3` nur maximal 3 Zeilen abgeben.

## INDEX

Ein Index macht, dass Daten im Hintergrund in eine spezielle Struktur gesetzt werden. Sie sind wie eine Suchhilfe für ein bestimmtes Attribut und können im join, where und order by verwendet werden. Da diese Befehle relativ lange sein können (vorallem bei grossen DBs), kann die Verwendung von Indexen einen grossen Unterschied machen.

Einen Index hinzufügen kann man folgendermassen `ALTER TABLE <table_name> ADD INDEX <index_name> (<attributname>)` genau so kann man mit `DROP INDEX` auch welche löschen.