#ÜK
#datenbanken

# Struktur und Daten einer DB verändern

## DDL - Data Definition Language

### Tabelle Verändern

Mit dem `ALTER`-Befehl kann man Attribute einer Tabelle nach dem erstellen hinzufügen oder löschen. Ein `ALTER`-Befehl beginnt immer mit `ALTER TABLE <tabellen_name>`. Darauf gibt es dann ein paar Variationen:

- `ADD COLUMN <spalten_name> <datentyp> [FIRST|AFTER <column_name_2>]`->Fügt eine neue Spalte hinzu
- `CHANGE COLUMN <spalten_name> <spalten_name_neu> <datentyp_neu>`-> Ändert den Namen und Datentypen einer Spalte
- `DROP COLUMN <spalten_name>`-> Löscht eine Spalte

### Tabelle / Datenbank Löschen

- `DROP TABLE <tabellen_name>` löscht eine Tabelle
- `DROP DATABASE <datenbank_name>` löscht eine Datenbank

## DML - Data Manipulation Language

### Bestehende Werte verändern

- `UPDATE <tabellen_name> SET <spaltenname_x> = "neuer Wert" WHERE <spaltenname_z> = "xyz"`

### Werte in der Tabelle löschen, aber Tabelle behalten

- `DELETE FROM <tabellen_name> WHERE ...` ← Ohne `WHERE` werden *alle* Inhalte gelöscht.

## DQL - Data Query Language (Gezieltes Auslesen)

DQL beinhaltet alles mit Select. Es geht um das direkte Ansprechen einzelner Entitäten. Der Aufbau einer `SELECT`-Query sieht folgendermassen aus:

1. `SELECT <spaltenname>`
2. `FROM <tabellenname>`
3. `WHERE <bedingung>`
4. `AND <bedingung2>`
5. `OR <bedingung3>`

Mit `ORDER BY <spaltenname> ASC|DSC` kann man die gegebenen Daten auch sortieren.

# Datenmigration

## Ziele:

- Du kannst in MySQL Workbench Datenbanken in ein Dump File exportieren und später wieder herstellen (importieren)
- Du kennst den SQL Befehl, um Daten aus einer .csv-Datei in eine Datenbank zu importieren
- Du weisst auf was du achten musst, wenn du Daten aus einer .csv-Datei in eine Datenbank importierst

Will man Daten aus zb. einer Excel-Tabelle in eine Datenbank migrieren, muss man diese zuerst in eine CSV-Datei umwandeln. Danach kann man diese Datei mit folgendem Code importieren:

```sql
LOAD DATA INFILE <FILEPATH> INTO TABLE <table_name>
CHARACTER SET utf8mb4
FIELDS TERMINATED BY ";"      #Hier werden die Trennzeichen angegeben
LINES TERMINATED BY "\r\n"    #Hier wird das Newline-Zeichen angegeben
IGNORE 1 ROWS 
(id, name, vorname); 
```

# Daten-Dump

Um einen Daten-Dump zu erstellen, muss man das “Data Export”-Fenster öffnen und dort die Daten exportieren.

Man muss auf den Administration-Tab gehen, “Data Export” anklicken, DB auswählen. Darauf “Dump Structure and Data” unten rechts auswählen. Wichtig ist, “Include Create Shema” und “Create Dump in a single Transaction” auszuwählen.