#schule 
#m164
# Lernziele

- Sie verstehen die Befehle `INSERT`, `UPDATE`, `DELETE`
- Sie können einfache CRUD-Operationen durchführen
- Sie können CRUD-Operationen durchführen, die einen oder mehrere Datensätze betrifft
- Sie können komplexe CRUD-Operatoren durchführen, die einen und mehrere Datensätze betrifft
- Sie können komplexe CRUD-Operationen durchführen (zB. mit Sub-Select)

# INSERT

Mit diesem Befehl ist es leicht möglich,  einer Tabelle einen neuen Eintrag hinzuzufügen.

```sql
INSERT INTO <tabellenname>
[(<liste mit Spalten>)]
VALUES (<liste mit werten>);

INSERT INTO Orte
	(PLZ, Ort)
	VALUES (33016, "Töröö");
```

# UPDATE

Mit Update kann man Datensätze einer Tabelle bearbeiten

```sql
UPDATE <tabellenname>
	SET <spalte1> = <wert1>
	WHERE ...

UPDATE Orte
	SET PLZ = 3018
	WHERE Ort = "Töröö";
```

## UPDATE mit Subselect

Es kann vorkommmen, dass in der `WHERE`-Bedingung des `UPDATE`-Befehls weitere Tabellen verwendet werden müssen. Dafür verwendet man Subselects, denn man kann beim dieser Art von Befehl keine `JOIN`-Statements verwenden. 

Beim Subselect ist wichtig, dass es mehr als einen Wert zurück gibt. Wenn “=” nicht funktioniert, kann man auch das `IN`-Kennwort verwenden.

Beispiel Subselect:

```sql
UPDATE <tabellenname>
	SET <attribut> = (SELECT ID FROM <tabelle2> 
											WHERE <attribut> = <wert1>)
WHERE <attribut> = (SELECT ID FROM <tabelle2>
											WHERE <attribut> = <wert1>)
```

Dieses Beispiel setzt das Attribut aller Einträge zum “wert1”, wo dieses Attribut momentan den “wert2” hat.

# DELETE

Beispiel

```sql
DELETE FROM <tabellenname> 
	WHERE ...
```

Zur Sicherheit sollte man immer zuerst einen Select-Befehl mit der gleichen `WHERE`-Klausel ausführen. So kann man sicher sein, dass nur gewollte Daten manipuliert werden!

Auch beim Löschen von Daten kann man Subselects verwenden!