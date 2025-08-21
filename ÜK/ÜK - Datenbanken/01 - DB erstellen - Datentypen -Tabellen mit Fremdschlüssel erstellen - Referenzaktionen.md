#ÜK
#datenbanken

# DB mit Daten erstellen

## Ziele

- Grundfunktionen zum erstellen einer Datenbank mit Tabellen verwenden
    - Data Definition Language (DDL)
- Grundfunktionen zum Abfüllen der Tabelle mit Daten verwenden
    - Data Manipulation language (DML)
- Grundfunktionen zum Auslesen der Daten einer Tabelle verwenden
    - Data Query Language
- SQL Queries in MySQL Workbench ausführen

## DDL - Data Definition Language

DDl wird verwendet, um Datenbanken anzulegen. Man verwendet immer mindestens eine eigende Datebank für ein Projekt, evtl. auch mehrere. Vorallem verwendet man nie eine Datenbank für mehrere Projekte

Datenbank kreieren: `CREATE DATABASE datenbank_name;`

Datenbank auswählen: `USE datenbank_name;`

Einzene Datenbanken anzeigen: `SHOW DATABASES;`

Mit explain die definierten Attribute anzeigen: `EXPLAIN tabellen_name;`

Tabelle erstellen: `CREATE TABLE person (id INT PRIMARY KEY AUTO_INCREMENT, beispiel1 VARCHAR(20), beispiel2 VARCHAR(20), beispiel3 INT(3))`

## DML - Werte einfügen

Mit dem folgenden Befehl kann man eine Tabelle mit Einträgen befüllen. Man kann die Namen der Attribute auch nicht angeben, aber dann muss man nach dem `VALUES`-Keyword für *alle* Attribute einen Wert angeben (Die werde der Reihe nach wie sie in der Tabelle stehen eingefügt).

`INSERT INTO tabellen_name (Attribut1, Attribut2) VALUES (value1, value2)`

# Datentypen

## Ziele

- Du kennst die verschiedenen Datentypen in einer Datenbank
- Du setzt die korrekten Datentypen ein
    - Zahlenformate
    - Textformate
    - Date / Time
- Du kannst ein Passwort verschlüsselt auf der DB ablegen

## Zahlen

### Ganzzahlen


Ein INT ist immer 4 bytes gross. Wenn man z.B, INT(3) schreibt, werden nur 3 Stellen dieser INT angezeigt, aber im Speicher hat sie dennoch die volle Grösse.

`UNSIGNED` wird für Zahlen ohne Vorzeichen verwendet (ohne Minusbereich). Man setzt es vor die Definition des Datentyps, bsp: `UNSIGNED INT(2)`

### Kommazahlen


## Textformate

`CHAR` hat eine festgelegte Länge, die immer voll verwendet wird.

`VARCHAR` hat einge flexible Länge bis zum Maximum und nutzt nur so viel Platz wie nötig

## Date & Time

Normalerweise wird TIME verwendet. Man kann aber auch TIME(3) machen, um die Zeit noch präziser, mit Kommastellen, anzugeben.

## DEFAULT / ON UPDATE

Mit diesen Keywords kann man festlegen, dass bestimmte Werte beim erstellen eines neuen DB-Eintrags automatisch ausgefüllt werden. ZB: `TIMESTAMP DEFAULT CURRENT_TIMESTAMP`

## Weitere Datentypen (BOOL / ENUM / BLOB)

`BOOL` → Gleich wie TINYINT(1), also ist 0 *false* und der Rest *true*

`ENUM` → Liste von möglichen Werten

`BLOB` → Dateien (zB. Bilder)

## Passwort Hashing

Um einen Wert, den man in die Datenbank eintragen will, zu verschlüsseln, muss man den Wert folgendermassen schreiben: `sha2("Mein Wert", 512)`. Sha2 ist ein Algorithmus, der diesen Wert verschlüsseln wird.

# Tabelle mit Fremdschlüssel erstellen & Referenzaktionen

## Ziele

- Du kannst Verknüpfungen zwischen Tabellen mit der Data Definition Language (DDL) definieren
- Du entscheidest, welche Folgen das Editieren und Löschen von “verknüpften” Daten hat

! Beim erstellen einer Datenbank ist es sinnvoll, immer zuerst die Tabellen ohne Fremdschlüssel und danach die Tabellen mit Fremdschlüssel zu erstellen.

## Fremdschlüssel erzeugen

## Parent-Child-Relationships

Parent ist die Tabelle, die den Primärschlüssel enthält. Child ist die Tabelle, die den Fremdschlüssel der Parent-Tabelle enthält.

## Referenzaktionen

Man kann definieren, was mit dem FK passiert, wenn der zugehörige PK gelöscht wird. Das wird eine Referenzaktion genannt und es gibt die folgenden fünf Möglichkeiten:

1. `set null`
    
    Wenn ein FK keine Referenz mehr hat, wird er auf NULL gesetzt. Das ist nicht ideal, da die Integrität verletzt wird und die Datenbank in einen undefinierten Zustand gerät.
    
2. `set default`
3. `cascade`
    
    Cascade bedeutet, dass bei einer Änderung oder Löschung auch alle zugehörigen Werte in der Kindtabelle gelöscht / geändert werden. Dadurch behält die Datenbank ihre Integrität.
    
4. `no action`
    
    No action ist der default in SQL. Dabei wird das ändern oder löschen des Schlüssels verhindert, solange noch Abhängigkeiten bestehen. Dadurch behält die Datenbank ihre integrität und es können keine Daten versehentlich gelöscht werden.
    
5. `restrict`

## CASACADE

Mit CASCADE kann man einen lösch- und/oder einen update-Befehl an andere Tabellen weiterleiten, sodass Einträge mit passenden Fremdschlüssen ebenfalls verändert werden.