#schule 
#m162
# Lernziele

1. Sie wissen, was SQL ist und kennen dessen Möglichkeiten
2. Sie kennen den SELECT-Befehl in Theorie und Praxis
3. Sie kennen die WHERE-Klausel in Theorie und Praxis
4. Sie können eigene Abfragen formulieren (mit einer Tabelle) und Aufgaben lösen

Joins werden verwendet, um Informationen, die auf mehrere Tabellen verteilt sind, in einer (temporären) Tabelle darzustellen.

# Arten von Joins

![Untitled](Schulmodule/M162%20-%20Datenbanken/Fotos%20&%20PDFs/Untitled%202.png)

## Inner Join

Beim Inner Join werden nur Datensätze zuück gegeben, die in beiden Datensätzen vorkommen.  Welche Datensätze das sind, wird in der ON-Klausel definiert.

![Untitled](Schulmodule/M162%20-%20Datenbanken/Fotos%20&%20PDFs/Untitled%201%201.png)

### Beispiel

```sql
SELECT l.Vorname, l.Nachname, l.Strasse, o.PLZ, o.Ort
FROM Lernende AS l
INNER JOIN Orte AS o
ON l.ort_id = o.id;
```

Retourniere nur Datensätze aus der Tabelle Lernende, in denen ein Fremdschlüsselwert `ort_id` vorhanden ist und ergänze die Ausgabe mit der Postleitzahl und dem Ort aus der Tabelle “Orte”

- Das normale `Join` ist dasselbe wie `INNER Join`
- `INNER JOIN` retourniert Teilmengen von Tabellen, falls *nicht* alle Datensätze die ON-Klausel erfüllen
- Erfüllen alle Datensätze einer Tabelle die ON-Klausel, wird die Tabelle vollständig retourniert

## Left Join

Beim Left Join werden alle Datensätze der linken Tabelle zurück gegeben während von der rechten Tabelle nur diese zurück gegeben werden, die mit der ON-Klausel gefiltert werden.

Es zeigt also eine gesamte Tabelle an, welche mit dem Inhalt einer anderen Tabelle ergänzt wird.

![Untitled](Schulmodule/M162%20-%20Datenbanken/Fotos%20&%20PDFs/Untitled%202%201.png)

Um zu prüfen, ob ein Left Join nötig ist, muss man abklären, ob es Fälle gibt, in denen Inhalte der Tabelle 2 nicht in der Tabelle 1 vorkommen. Also wenn es Primärschlüssel der Tabelle 1 gibt, die in der Tabelle 2 keine Fremdschlüssel haben, braucht es das Left Join, um alle Inhalte zu sehen.

### Beispiel

```sql
SELECT l.Vorname, l.Nachname, l.Strasse, f.Firma
FROM Lernende AS l
LEFT JOIN Firmen AS f
ON l.firma_id = f.id
ORDER BY l.Vorname
```

Retourniere alle Datensätze der linken Tabelle *Lernende*, egal ob ein Fremdschlüsselwert *firma_id* vorhanden ist oder nicht. Falls ein Fremdschlüsselwert vorhanden ist, dann ergänze die Ausgabe mit den Daten aus der Primärtabelle dieses schlüssels.

## Right Join

Beim Right Join wird die rechte Tabelle vollständig ausgegeben. Die Linke Tabelle aber wird bei Werten importiert, die die ON-Klausel erfüllen.

Right Join ist mit SQLite nicht möglich! Man kann aber ein Left Join verwenden und die Tabellen vertauschen!

![Untitled](Schulmodule/M162%20-%20Datenbanken/Fotos%20&%20PDFs/Untitled%203.png)

### Beispiel

```sql
SELECT l.Vorname, l.Nachname, l.Strasse, o.PLZ, o.Ort
FROM Lernende AS l
RIGHT JOIN Orte AS o
ON l.fk_oid = o.oid;
```

Retourniere die Datensätze aus der Tabelle *Lernende*, in denen ein Fremdschlüsselwert *ort_id* vorhanden ist und ergänze die Ausgabe mit der Postleitzahl und dem Ort aus der Tabelle *Orte*. Zusätzich sollen alle Orte aufgeführt werden, in denen kein Lernender wohnt.

## Full Outer Join

Beim Full Outer Join werden die Daten beider Tabellen geliefert. Wenn Einträge der Tabellen nach der Verknüpfungstabelle zusammenpassen, werden sie zusammengeführt und als eine Zeile ausgegeben. Ansonsten werden sie mit NULL-Werten dargestellt.

Full Outer Join ist nicht in SQLite implementiert!!!

Darum muss man für das gleiche Ergebnis viel mehr Zeilen schreiben.

![Untitled](Schulmodule/M162%20-%20Datenbanken/Fotos%20&%20PDFs/Untitled%204.png)

### Beispiel

```sql
SELECT l.Vorname, l.Nachname, l.Strasse, o.PLZ, o.Ort
FROM Lernende AS l
LEFT JOIN Orte AS o
ON l.ort_id = o.id
UNION SELECT l.Vorname, l.Nachname, l.Strasse, o.PLZ, o.Ort
FROM Orte AS o
LEFT JOIN Lernende AS l
ON l.ort_id = o.id
ORDER BY Ort;
```

Retourniere alle Datensätze der linken Tabelle *Lernende*, egal ob ein Fremdschlüsselwert *fk_oid* vorhanden ist oder nicht. Ergänze die Ausgabe mit allen Orten, an denen kein Lernender wohnt. Dann sortiere die Ausgabe nach Ort aufsteigend.

## UNION

Mit UNION können zwei Ausgaben zu einer Tabelle zusammengeführt werden, wenn die Attributlisten identisch sind.

Man könnte UNION beispielsweise benutzen, um die Informationen von Lehrern und Schülern auf einer Tabelle anzuzeigen.