#schule 
#m164
# Lernziele

- Sie können eine Datenbank erstellen
- Sie können alle Tabellen in der Datenbank erstellen
- Sie können Änderungen an der Tabellenstruktur vornehmen
- Sie können Constraints definieren

# Datenbank erstellen

`create database <name>` ist der Befehl, mit dem man eine neue Datenbank erstellt. Man kann an diesen Befehl optional auch ein `collate` anhängen, welches die Sortierreihenfolge genau definiert: `create database <name> collate Latin1_General_100_CI_AI_SC_UTF8`.

Es gibt viele verschiedene Befehle, die man mit einem `collate` mitgeben kann…

Man kann mit `alter database <name> collate <spezifikationen>` die bestehende Kollation der Datenbank verändern

Beim Erstellen einer Datenbank ist es äusserst wichtig, zuerst die Tabellen mit Primärschlüsseln und erst danach die Tabellen mit Sekondärschlüsseln zu erstellen.

Erstellt wird eine Tabelle mit dem Befehl `create table <name>` 

# Datenbank Löschen

Mit `drop database <name>` kann man eine bestehende Datenbank löschen.

# Auto Increment

Mit dem `auto increment`-Parameter überlässt man das Einfüllen der Werte dem Computer. Wenn zB. ein neuer Primärschlüssel hinzugefügt wird, hat der automatisch einen Wert, der dem höchsten Schlüsselwert plus eins entspricht.

## Vorteil

Der Vorteil von diesem Parameter ist, dass einem beim Eintragen der Daten viel Arbeit erspart wird. Bei tausenden Daten will man ja nicht jeden Primärschlüssel einzeln eintragen müssen.

## Nachteil

Der Nachteil von diesem Parameter ist, das man bei einem Fehler keine möglichkeit zum Eingreifen hat. Der PC hat volle Kontrolle über die Schlüsselwerte.

# Create Table

Eine Tabelle erstellen kann man mit folgendem Befehl:

```sql
create table <name_datenbank>.<name_schema>.<name_tabelle>(
	ID int IDENTITY(1, 1) PRIMARY KEY AUTO_INCREMENT
	<spalte1> <datentyp> NOT NULL,
	<spalte2> <datentyp> NOT NULL
	...
```

![Untitled](Schulmodule/M164%20-SQL/Fotos%20&%20PDFs/Untitled.png)

# Create Table mit Foreign Key

Um eine Tabelle mit foreign key zu erstellen, muss selbstverständlich die Tabelle mit dem Primary Key bereits existieren. Ein Foreign Key wird folgendermassen hinzugefügt:

```sql
<spaltenname> <datentyp> FOREIGN KEY REFERENCES <Primärtabellenname>(<name_des_primärschlüssels>) 
ON DELETE <bedingung>
```

Das `on delete` bestimmt, wie die Tabelle reagiert, wenn der Primary Key gelöscht wird. Im oberen Beispiel wird der Fremdschlüssel darauf auf “*null*” gesetzt.

## ON DELETE & ON UPDATE - Regeln

- NO ACTION
    - Erlaubt das Löschen des Primarschlüssels nur dann, wenn dieser in keiner Detailtabelle benutzt wird.
- CASCADE
    - Ein DELETE in der Primärtabelle führt zu einer Löschung in der Detailtabelle
- SET NULL
    - Ein DELETE in der Primärtabelle setzt die entsprechenden Fremdschlüssel zu “*null”*
- SET DEFAULT
    - Setzt den Wert des Fremdschlüssels auf den default-Wert. Falls keiner angegeben ist, wird dieser Wert auf “*null”* gesetzt

## Wann wird welche ON DELETE-Reggel empfohlen

- 1:mc
    - NO ACTION → Bsp: Ein Ort soll nicht gelöscht werden, solange noch eine Person dort wohnt.
- c:mc
    - SET NULL oder DEFAULT → Bsp: Eine Firma kann gelöscht werden & alle Verweise auf die Firma werden darauf auf “*null*” gesetzt.
- mc:mc
    - CASCADE → Bsp: Wenn ein Lernender gelöscht wird, werden die Einträge dieses Lernenden in der Zischentabelle auch gelöscht.

# ALTER TABLE

Eine bestehende Tabelle kann man mit dem `alter table`-Befehl bearbeiten:

### Attribut hinzufügen

`ALTER TABLE <name> ADD <spaltenname> <datentyp>`

### Attribut ändern

`ALTER TABLE <name> ALTER COLUMN <spaltenname> <datentyp>`

### Attribut löschen

`ALTER TABLE <name> DROP COLUMN <spaltenname>`

### Fremdschlüssel hinzufügen

`ALTER TABLE <name> ADD CONSTRAINT <constraint> FOREIGN KEY (fremdschlüssel)`

`REFERENCES <primärtabellenname> (primärschlüsselname)`

`ON DELETE <verhaltensregel>;`

- Constraint → Name des zukünftigen Fremdschlüssels
- Fremdschlüssel → Name des Fremdschlüsselattributes in der Detailtabelle

### Fremdschlüssel löschen

`ALTER TABLE <tabellenname> DROP CONTRAINT <constraintname>`

### Eindeutigen Schlüssel hinzufügen

`ALTER TABLE <tabellenname> ADD UNIQUE (<spaltenname>)`

### Eindeutigen Schlüssel löschen

`ALTER TABLE <tabellenname> DROP CONSTRAINT <constraintname>`

Standartwert festlegen

`ALTER TABLE <tabellenname> ADD CONSTAINT <constraint> DEFAULT 0 FOR <spaltenname>;`

### Standartwert löschen

`ALTER TABLE <tabellenname> ALTER COLUMN <spaltenname> DROP DEFAULT`

### Wertebereich festlegen

`ALTER TABLE <tabellenname> ADD CONSTRAINT <constraintname> CHECK (ausdruck)`

Der Ausdruck bei diesem Befehl definiert den Wertebereich und könnte folgendermassen aussehen → (PLZ ≥ 1000 AND PLZ ≤ 9999)

### Wertebereich löschen

`ALTER TABLE <tabellenname> DROP CONSTRAINT <constraintname>;`