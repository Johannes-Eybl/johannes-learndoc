#schule 
#m162
# `SELECT`

Der SELECT-Befehl wird dazu genutzt, Daten aus einer Tabelle zu holen. Es gibt einige optionale Erweiterungen dieses Befehls, die unter Anderem dabei helfen, die gesuchten Daten zu filtern oder Daten aus verschiedenen Tabellen zusammen zu führen.

Die einfachste Version des Befehls sieht folgendermassen aus:

`SELECT *attribut* FROM *tabellenname*`

Man kann aber auch mehrere Attribute, mit Komma getrennt, angeben.

Wenn man mit Attributen arbeitet, die Integer sind, kann man auch mit Mathematischen Operatoren wie `+` oder `*` arbeiten. Beispiel:

`SELECT preis * 0.8 FROM products`

## Optionaler Syntax des `SELECT`-Befehls

- `DISTINCT`/`ALL`
    
    Das `DISTINCT`-Schlüsselwort filtert aus den Ergebnissen des `SELECT`-Befehls alle Wiederholungen, so dass jeder Wert beim Ergebnis nur ein mal vorkommt. Beispiel:
    
    `SELECT DISTINCT name FROM schüler` würde wiederholte Namen streichen, jeder Name käme nur ein mal vor.
    
    `ALL` ist bei der `SELECT`-Suche der Standard und muss darum nicht ausgeschrieben werden.
    
- `LIMIT <zahl>`
    
    Mit diesem Befehl kann man angeben, wie viele Werte zurück gegeben werden sollen. Wird am Ende eines `SELECT`-Befehls angeschlossen
    
- `*`
    
    Das `*`-Symbol steht für “alle” und kann anstelle von Attributnamen verwendet werden, um jedes mögliche Attribut zu wählen
    
- `|| ||`
    
    Der `|| ||` - Wert wird dazu genutzt, mehrere Attribute in eine Spalte zusammen zu führen. Zwischen den  Strichen kann ein String gesetzt werden, der dann zwischen den Attributwerten sitzt. Beispiel:
    
    `SELECT vorname || " " || nachname FROM schüler` gibt eine einzige Spalte zurück, in der Vor- und Nachnamen mit einem Leerschlag getrennt gelistet sind.
    
- `AS`
    
    `AS` wird verwendet, um bei der Ausgabe den Titel von Spalten zu ändern. Das ist zum Beispiel nützlich, wenn man mehrere Spalten mit `||` zusammen führt. Der `AS`-Syntax wird im Befehl direkt nach dem Attributnamen geschrieben, so wie im folgenden Beispiel:
    
    `SELECT vorname AS "Surname", plz AS "Postleitzahl" FROM kunden`
    
- `SUM(<Attribut>)`
    
    Gibt die Summe der Attributwerte zurück, insofern das ein Integer ist. Bsp: `SELECT SUM(preis) FROM products` ← Returnt den Gesamtpreis aller Produkte
    
- `AVG(<Attribut>)`
    
    Gibt den Durchschnittswert aller Werte eines Attributs zurück
    
- `COUNT(<Attribut>)`
    
    Gibt die Anzahl der Werte (Zeilen) des gegebenen Attributs zurück
    
- `MIN(<Attribut>)` und `MAX(<Attribut>)`
    
    Gibt nur den tiefsten oder den höchsten Attributwert zurück.
    
- `ORDER BY <Attribut>`
    
    Sortiert die Ausgabe nach einem bestimmten Wert wie zum Beispiel: `SELECT * FROM products ORDER BY price`
    
- `ASC` und `DESC`
    
    Bestimmt, ob auf- oder absteigend sortiert wird. Asc ist Standard und muss darum nicht geschrieben werden. Wird beim `ORDER BY` nach dem Attribut verwendet (`ORDER BY price DESC`)
    

# `WHERE`

Mit dem `WHERE`-Keyword kann man `SELECT`-Suchen filtern. 

Operatoren für das Filtern von Daten:

- `=` und `<>`
    
    Gleich, kleiner und grösser. `<>` ist das Gegenteil von `=` und schliesst also einen bestimmten Wert von der Suche aus (`NOT` macht das selbe!)
    
- `<`, `>`, `<=` und `=>`
    
    Aus Python bekannt schliessen diese Zeichen bestimmte Werte ein- oder aus. Man kann die Werte auch auf Buchstaben anwenden, wobei a<b…<z gilt. Bei Buchstaben ist der Input Case-Sensitive, sollte immer gross geschrieben werden!
    
- `AND` und `OR`
    
    Mit diesen Operatoren kann man mehrere Sachen filtern, bzw mehrere Filter-Konditionen erlauben. Wie in Python.
    
- `NOT`
    
    Dieser Operator lässt einen bestimmte Operatoren umkehren, so dass zum Beispiel alles ausser ein Wert angezeigt wird. Ist dasselbe wie der `<>`-Operator.
    
- `BETWEEN <wert1> AND <wert2>`
    
    Lässt einen für Werte zwischen x und y suchen. Beispiel: `SELECT * FROM schüler WHERE jahrgang BETWEEN 2000 AND 2003`
    
- `LIKE`
    
    Mit `LIKE` kann man beim Filtern Platzhalter verwenden um zum Beispiel nach Teilen von Strings oder bestimmten Zahlenfolgen zu suchen. Es gibt mehrere Arten von Platzhaltern:
    
    - `%` → Beliebig viele Zeichen
        - `... WHERE nachname LIKE "Müll%"` → Sucht nach allen Nachnamen, die mit “Müll” beginnen.
    - `_` → Ein Zeichen
        - `... WHERE jahr LIKE "200_"` → Sucht nach allen Jahren, die zwischen 1999 und 2010 liegen.
    
    Man kann mit `_` eine bestimme Anzahl von Zeichen angeben, während `%` für eine beliebige Anzahl Zeichen steht (min. 1)
    
- `IS NULL`
    
    Mit diesem Operator kann man nach fehlenden Datensätzen suchen. Beachte, dass `NULL != ""`!!!
    

# `GROUP BY`

Wenn wir alle Wohnorte der Lernenden ausgeben wollen, können wir folgende Abfrage verwenden:

`SELECT DISTINCT Ort FROM Lernende;`

Eine zweite Möglichkeit, die dasselbe Ergebnis liefert, ist folgende Abfrage:

`SELECT Ort FROM Lernende GROUP BY Ort;`

Was ist der Sinn von GROUP BY (warum kompliziert, wenn es auch einfacher geht)? Diese Klausel wird v.a. dafür verwendet, gruppenweise Auswertungen durchzuführen (Aggregatsfunktion), was mit DISTINCT nicht möglich ist.

`SELECT Ort, AVG(2021-Jahrgang) AS "Durchschnittsalter" FROM Lernende GROUP BY Ort;`

- **>** Das durchschnittliche Alter der Lernenden pro Ort wird ausgegeben.