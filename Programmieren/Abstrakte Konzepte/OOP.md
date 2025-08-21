# Was ist OOP
Oop ist eine Programmiermethodik, bei der man ein Programm in viele einzelne Teile trennt, die möglichst unabhängig voneinander funktionieren.
Die Definition der einzelnen Teile nennt man "Klasse". Eine Klasse kann mehrmals eingesetzt (instantiiert) werden, jedes mal wird eine Kopie generiert, welche man auch 'Objekt' nennt.

Wenn das Programm gut geschrieben ist, sind die Objekte von einander abgekapselt und enthalten nur die Daten, welche für sie relevant sind (Verkapselung).
# Wofür wird es gebraucht
Oop erlaubt für bessere Wartbarkeit und Austauschbarkeit der vielen Aspekte eines Programms. Dadurch kann man als Team effizienter arbeiten.
# Klassen
Sind Baupläne für Objekte. Sie beschreiben, was für Werte und Methoden das Objekt enthalten wird. Zb. würde die Klasse "Mensch" Werte wie Grösse, Gewicht, Name und Alter erhalten. Diese würden aber erst bei der Instantiierung fest gelegt werden.
# Objekte / Instanzen
Ein Objekt wird anhand von dem Bauplan (der Klasse) erstellt. Die Erstellung (oder auch Instantiierung genannt) sorgt dafür, dass die Attribute gesetzt werden.

Ohne das *static*-Keyword wird aus einer Klassenmethode eine Instanzenmethode, bzw. Instanzenvariabel. 
## Instanzen erzeugen
Ein neues Objekt wird mit dem *new-*Operator gemacht. `Point p1 = new Point();` bedeutet, dass die Variabel p1 nun eine Referenz auf eine Instanz der Klasse Point enthält. Datentyp ist diese Klasse. 