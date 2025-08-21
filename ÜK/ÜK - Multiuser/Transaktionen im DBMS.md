#ÜK
#multiuser

# Ziele

- Anforderungen an das Datenbankmanagementsystem bezüglich Multi-User-Fähigkeit kennen
- Wissen, wie man Transaktionen im DBMS sicherstellt
- Isolationsprobleme auf Datenbankebene kennen
- Verschiedene Isolationslevel kennen
- Vier ACID-Kriterien aufzählen

# Definition Transaktion

Eine Transaktion ist eine Folge von Programmschritten, die den Datenbestand nach einer Ausführung in einem konsistenten Zustand hinterlassen. Aus diesem Grund muss eine Transaktion entweder fehlerfrei und vollständig oder gar nicht ausgeführt werden.

Praktisch wird vor einer Veränderung der Datenbank ein Savepoint kreiert, zu dem die Tabelle nach einem Fehler zurückgesetzt werden kann.

In SQL werden dazu folgende Statements verwendet:

`START TRANSACTION` oder `BEGIN` → Neue Transaktion starten

`COMMIT` → Änderungen persistieren

`ROLLBACK` → Änderungen verwerfen

`SET autocommit` → Autocommit-Modus für die aktuelle Session ändern

# ACID

## A → Atomicity

Transaktionen werden ganz oder gar nicht ausgeführt. Bei Abbruch bleibt die DB unverändert.

## C → Consistency

Nach einer Veränderung ist der Datenbestand konsistent.

## I → Isolation

Gleichzeitig ausgeführte Transaktionen dürfen sich nicht gegenseitig beeinflussen. Parallele Transaktionen “erscheinen” seriell. Es gibt verschiedene Isolationsstufen, die eingestellt werden können.

## D → Durability

Änderungen von Transaktionen bleiben dauerhaft gespeichert. Systemfehler dürfen die dauerhafte Speicherung nicht verhindern.

# Isolationsprobleme

## Lost Update

Wenn zwei Nutzer gleichzeitig Veränderungen am selben Datensatz vornehmen wollen, wird nur die Änderung einer Transaktion übernommmen.

## Dirty Read

Daten einer nicht abgeschlossenen Transaktion werden von einer anderen Transaktion gelesen. Wenn die nicht abgeschlossene Transaktion zurückgesetzt wird (Rollback), sind die gelesenen Daten invalide.

## Non-Repeatable-Read

Passiert, wenn zwischen zwei Lesevorgängen Daten geupdatet werden. Die beiden reads haben unterschiedlichen Inhalt.

## Phantom Read

Wenn Zwischen zwei Lesevorgängen, die Resultate Filtern, wegen einem zwischendurch passiertem Update unterschiedliche Anzahl von Resultaten geliefert werden.

# Isolationslevel

## Read uncommitted / Dirty Read

Uncommittete Daten von anderen Transaktionen werden gelesen. Bei einem SELECT wird kein Lock gemacht.

## Read commited

Nur committete Daten werden gelesen. Jedes SELECT hat einein eigenen Snapshot.

## Repeatable Read

Ein SELECT-Statement gibt immer die gleichen Daten aus dem gleichen Snapshot zurück.

## Serializable

Transaktionen werden so ausgeführt, als währen sie nach einander.

![Untitled](ÜK/ÜK%20-%20Multiuser/Multiuser%20-%20PDFs%20&%20Fotos/Untitled%206.png)