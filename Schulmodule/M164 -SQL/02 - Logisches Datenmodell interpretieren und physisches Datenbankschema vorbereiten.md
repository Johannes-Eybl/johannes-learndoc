#schule 
#m164
# Lernziele

- Sie kennen alle Datentypen Ihres RDMBS
- Sie kennen alle Beziehungstypen eines relationalen Datenmod3ells
- Sie wissen, welche Beziehungstypen in einem RDBMS möglich sind
- Sie wissen, wie Beziehungen in einem RDBMS abgebildet werden (Primär- und Fremdschlüssel)
- Sie kennen und bestimmen weitere Constraints
- Sie kennen Zeichensätze und legen sich auf einen fest
- Sie wissen, was Indizes sind und wann diese Sinn machen

# Beziehungen

Bei Beziehungen gibt es immer eine Primär- und eine Detailtabelle. 

- 1 → Einfache Assoziation, genau eines
- c → konditionelle Assoziation, null oder eines
- m → Komplexe Assoziation, eines oder mehrere
- mc → Konditionell-komplexe Assoziation, sprich 0, 1 oder mehrere

# Mögliche Beziehungstypen

- eins zu eins → 1:c
- eins zu viele → 1:mc oder c:mc
- viele zu viele → mc:mc

# SQL Datenbanksprachen

Die Sprache SQL wird generell in drei Gebiete unterteilt:

## Data Definition Language (DDL)

- Datenbanken erstellen → `create database`, `create table`
- Tabellen ändern → `alter table`
- Datenbanken und Tabellen löschen → `drop database`, `drop table`
- Primärschlüssel definieren → `primary key`
- Fremdschlüssel definieren → `foreign key`
- Regeln für Attributwerte festlegen → `constraint`
    - Zb. Primär- und Fremschlüsselbeziehung
- Indexe → `create index`
- Stored procedures → `create procedure`

## Data Manipulation Language (DML)

- Daten erfassen → `insert`
- Daten ändern → `update`
- Daten löschen → `delete`
- Abfragen durchführen → `select`

## Data Control Language (DCL)

Mit dieser Subkategorie lassen sich Rechte auf Datenbanken oder Tabellen vergeben.

- Recht vergeben → `grant`
- Recht entziehen → `revoke`

# Datentypen

- int (tinyint, smallint, bigint) → Zahlen
- float → Kommazahlen
- double → Grosse Kommazahlen
- char → String mit fixer Länge
- varchar → String mit variabler Länge
- text → String mit sehr hoher Länge
- blob → binäre Daten wie zb. Bilder
- date → Datum
- time → Zeit
- timestamp → Datum und Zeit#

# Constraints

Constraints sind Regeln für Attributewerte, die den sicheren Umgang mit der Datenbank stärken.

- `NOT NULL` → Stellt sicher, dass keine “null”-Werte möglich sind
- `UNIQUE` → Stellt sicher, dass jeder Wert nur ein mal vorkommt
- `PRIMARY KEY` → Identifikationsschlüssel
- `FOREIGN KEY` → Referenz auf Primärschlüssel in der Primärtabelle
- `CHECK` → Schränkt den Wertebereich für ein Attribut ein.
    - Beispiel: `alter INT CHECK (alter >= 18)`
- `DEFAULT` → Lässt einen Standartwert für Attribute setzen, falls keines gegeben wird

# Indizes

Mit Indizes kann man Daten einer DB miteinander verknüpfen und so die Suchgeschwindigkeit deutlich steigern. Wenn zum Beispiel häufig nach einem bestimmen Attribut wie dem Namen gesucht wird, kann ein Index hillfreich sein. 

Ein Nachteil von Indizes ist, dass das Schreiben in die Datenbank verlangsamt wird. Immer, wenn ein neuer Eintrag gemacht wird, muss das System auch den Index updaten… Aus diesem Grund machen Indizes dann Sinn, wenn in einer DB häuffig gelesen und eher wenig geschrieben wird.