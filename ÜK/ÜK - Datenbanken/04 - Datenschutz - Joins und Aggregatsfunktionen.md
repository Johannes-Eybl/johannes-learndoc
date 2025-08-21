#ÜK
#datenbanken
# DCL- Data Control Language

DCL wird verwendet, um Benutzer und deren Rechte zu verwalten.

## Nutzer erstellen

`CREATE USER <benutzer@hostname> IDENTIFIED BY <password>;`

Dieser Befehl macht einen neuen Nutzer, der “Benutzer” heisst. Nach dem “@” wird der Hostname angegeben, von dem aus der Nutzer auf die Datenbank zugreiffen kann. Noch ein Beispiel:

`CREATE USER eybl@localhost IDENTIFIED BY pw1234` → Erstelle einen Nutzer “eybl”, der vom Localhost, also vom gleichen PC aus auf dem die Datenbank gespeichert ist, auf diese zugreiffen kann. Sein Passwort ist “pw12345”. Noch ein Beispiel:

`CREATE USER hr_manager@"%" IDENTIFIED BY "pw12345";`-> Erstelle einen Nutzer “hr_manager”, der das Passwort “pw12345” hat und von überall aus auf die DB zugreiffen kann (% steht für eine beliebige Folge an Characters).

## Rechte vergeben

`GRANT ALL ON <datenbank.tabelle> TO <nutzer@hostname>;` → Dieser Befehl gibt einem Nutzer alle Rechte für eine bestimmte Tabelle. Rechte vergeben kann aber nur *root*. Es gibt drei Bereiche, auf die sich vergebene Rechte beziehen können:

1. datenbank.tabelle → Um Rechte für eine bestimmte Tabelle zu verteilen
2. datenbank.* → Um Rechte für alle Tabellen einer Datenbank zu verteilen
3. “*” → * wird verwendet, wenn alles gemeint ist und schliesst alle Datenbanken (mit deren Tabellen) mit ein

Um verschiedene Rechte zu vergeben, gibt man einfach den Befehl ein, den man dem Nutzer möglich machen will. Beispielsweise kann man dem Nutzer folgendermassen Update-Rechte geben:

`GRANT UPDATE, DELETE ON * TO <eybl@localhost>;` → Dieser Befehl gibt dem Nutzer “eybl@localhost” das Recht, UPDATE- und DELETE-Befehle in allen Datenbanken auszuführen.

## Rechte entziehen

`REVOKE ALL ON * FROM eybl@localhost` → Dieser Befehl nimmt dem Nutzer “eybl@localhost” alle Rechte von allen Datenbanken. Ein weiteres Beispiel:

`REVOKE UPDATE ON firma.orte FROM eybl@localhost` → Dieser Befehl nimmt dem Nutzer “eybl@localhost” das Recht, in der Tabelle “Orte” updates durchzuführen.

## Nutzer löschen

`DROP USER benutzer@hostname;` → Dieser Befehl löscht den Nutzer “benutzer@hostname”. Es gibt aber auch eine zweite Möglichkeit, den Nutzer zu löschen:

`DELETE FROM [MYSQL.]USER WHERE user = benutzername;` → Dieser Befehl löscht den Nutzer aus der internen SQL-Tabelle, in der alle Nutzer gespeichert sind.

# Joins und Aggregationsfunktionen

# Ziele

- Du kannst SQL Abfragen über eine oder mehrere Tabellen
- Du verwendest Joins, wenn du SQL Abfragen über mehrere Tabellen erstellst
- Du weisst, dass du Werte auf null mit IS oder IS NOT vergleichen musst
- Du kannst SQL Abfragerestulate mit IN, NOT IN, BETWEEN, LIKE, NOT LIKE weiter verfeinern
- Du kannst SQL Aggregatsfunktionen COUNT, AVG, MAX, MIN, SUM verwenden
- Du kannst SQL Abfrageresultate mit GROUP BY gruppieren und mit HAVING weiter filtern

## Auf NULL prüfen

Mit JOIN kann man mehrere Tabellen als eine ausgeben. Um auf NULL zu prüfen schreibt man `... IS NULL` beziehungsweise `... IS NOT NULL`. 

## IN-Klausel

Mit `IN` kann man mehrere `OR`-Statements in eines zusammenfassen. Beispiel:

`SELECT * FROM mitarbeiter WHERE vorname IN ("Leon", "Luis")` 

Dieses Beispiel returnt alle Einträge, in denen der Vorname Leon oder Luis ist, also das gleiche wie bei `SELECT * FROM mitarbeiter WHERE vorname = "Leon" OR vorname = "Luis"`

## LIKE und NOT LIKE

`LIKE` wird verwendet, um nach einer Zeichenkette, bzw. einem Pattern zu suchen. Das bedeutet man nutzt es, wenn man mit `%` oder `_` sucht. 

## Between

Mit `between` kann man etwas zwischen Wert x und y suchen, wobei diese Werte entweder Zahlen, Text oder Buchstaben sind. Wert x ist inklusiv und Wert y ist exklusiv (wird nicht ausgegeben).

## Aggregatsfunktionen

Es gibt eine Reihe von Aggregatsfunktionen, welche alle einen berechneten Wert ausgeben. 

- COUNT()
- SUM()
- MIN(), MAX()
- AVG()

Diese Funktionen geben einen selbsterklärenden Wert zurück, welcher aus dem Attribut, das in der Klammer steht, berechnet wird. Da diese Funktionen immer genau einen Wert zurückgeben, kann man den Output nach einem Attribut x gruppieren. Das bedeutet, dass die Ausgabe die Aggregatsfunktion immer Gruppenweise auf alle Einträge mit dem selben Attribut x anwendet.

HAVING

Bei einer Aggregatsfunktion kann man den Output nach `GROUP BY x` weiter filtern. Das macht man mit `HAVING x` . Der Unterschied zu `WHERE` ist, dass `WHERE` jeden Eintrag einzeln filtert und `HAVING` die Gruppen von `GROUP BY` filtert.