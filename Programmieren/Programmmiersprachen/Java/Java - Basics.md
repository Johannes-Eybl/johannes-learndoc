#java 
#programming

[[OOP]]
# Basics

## Compiler

Ein Compiler übersetzt Source Code in Maschinen Code. Jeder Prozessortyp hat eigene Maschienencode-Befehle, weshalb der Compiler für verschiedene Typen compilen muss. 

## Interpreter

Ein Interpreter liest den Code “on the go”, übersetzt also erst bei der Ausführung zu Maschienencode.

## Wie es in Java funktioniert

In Java wird die .java-Datei (von der IDE) mit dem Compiler zu einer .class-Datei verwandelt. Diese .class-Datei wird dann bei der Runtime von einem Interpreter (Java Runtime Environment) zu dem Prozessorspezifischem Code gemacht, der benötigt wird. 

# Namenskonvention

- Java-Files fangen immer mit Grossbuchstaben an
- Classes fangen immer mit Grossbuchstaben an
- Package Names sind immer klein

# Programmier-Vocables (Deklaration/Inizialisierung, Casten)

### Deklaration

`String s;` bedeutet, dass eine Variabel in Existenz gebracht wird, aber ihr kein Wert gegeben wird.

### Inizialisierung

`s = "hi"` inizialisiert eine Variabel, das bedeutet ihr wird ein Wert zugewiesen

### Casten

Wenn man Datentypen konvertiert. Beim Konvertieren muss man zwischen impliziten und expliziten Casten unterscheiden. 

### Implizites Casten

Beim impliziten Casten kann die Programmiersprache automatisch zwischen den Datentypen wechseln, weshalb der Programmierer nichts extra hinschreiben muss. 

Ein Beispiel für impliziertes Casten in Java ist das umwandeln von int zu string oder von int zu long, was automatisch erkannt und gemacht wird.

### Explizites Casten

Beim expliziten Casten muss der Programmierer etwas hinschreiben, um den Datentypen zu ändern. Das ist zum Beispiel beim Wechseln von Typen mit hohem Speicherverbrauch zu Werten mit tiefem Speicherverbrauch nötig.

Ein Beispiel für explizites Casten ist die Umwandlung von string zu int.

# Unit-Tests

*Unit Test werden verwendet, um die Anforderungen, die an eine Applikation gestellt werden, zu prüfen.*

Um Java-Test zu machen, wird das Jupiter-Framework verwendet, damit kann man einen Teil des Codes (zb. eine Methode) isolieren und nach erwarteten Werten prüfen. 

Unit tests werden nach dem A-A-A-Prinzip gemacht. Das steht für Arrange-Act-Assert.

1. Zuerst werden die Testdaten erstellt (zb. wird eine Instanz der Klasse oder ein beispiels-Array erzeugt)
2. Es wird die Methode aufgerufen, welche getested werden muss
3. Mithilfe der Assert()-Methode wird das Ergebnis/Resultat der Methode mit der Erwarteten Rückgabe verglichen.

Damit das Testen möglich wird, muss man zuerst die Jupiter-Testing Library importieren:

`import org.junit.jupiter.api.Test;`

## Die Assert()-Methode

[Die gesamten asserts sind hier zu finden](https://junit.org/junit5/docs/5.0.1/api/org/junit/jupiter/api/Assertions.html). *Assert* bedeutet auf Deutsch “Behauptung” - es wird behauptet, dass zwei Werte gleich oder eben nicht gleich sind. Ist die Behauptung falsch gibt es einen Error und der Test schlägt fehl.

- `assertEquals(expectation, actual)` → Vergleicht einen erwarteten Wert mit einem Tatsächlichen. Gibt einen Error, wenn die Werte nicht gleich sind
- `assertNotEquals(unexpected, actual)` → Vergleicht einen nicht erwarteten Wert mit einem Tatsächlichen. Gibt einen Error, wenn die Werte gleich sind
- `assertArrayEquals(expected, actual)` → Vergleicht Arrays

## Parametrisierte Tests

Parametrisierte Tests erlauben es einem, eine Methode auf kompakte Weise mit mehreren Daten zu testen.

### Ein Beispiel

```java
@ParameterizedTest
@CsvSource({"0, 0", "12, 3", "0123, 6", "1000, 1"})
void quersum_MultipleHappyCases(String testData, String result){
	// Act
	int actual = StringExtensions.quersum(testData);
	
	// Assert
	// Needs the toString because the expected results are stored as Strings
	assertEquals(result, Integer.toString(actual));
}
```

In diesem Beispeil wird die `quersum()`-Methode mit verschiedenen Parametern getestet. Die `quersum_MultiplyHappyCases()`-Methode wird nur dazu verwendet, um den Test durchzuführen.

Mit `@CsvSource`, einem Array, wird definiert mit welchen Werten die `quersum_MUltiplyHappyCases()` Methode ausgeführt werden soll. In dem Array sind paare von Parametern als Strings gespeichert und die Methode wird für jedes Paar ein mal durchgeführt. So kann man mit einer Zeile eine mehrfache Wiederholung des Tests machen.

# Vererbung (This, Super, Abstract, Protected)

## super vs this

`this` ist eine Referenz auf die aktuelle Instanz

`super` ist eine Referenz auf die aktuelle Superinstanz

`protected` macht, dass alle Klassen, die im gleichen Package sind, so wie auch Subklassen (die, die von der Baseclass erben), diese Variabel sehen können. Gegenüber anderen Klassen ist es private.

`super` lässt einen in der Kindsklasse den Konstruktor einer Elternklasse auswählen und ändern.

`abstract` definiert eine Klasse als nicht instanziierbar. Das Wird verwendet, wenn die Klasse nur als Parent dient.

Man kann dieses Keyword auch für Funktionen verwenden. Diese Funktionen muss man in der Parent-Class deklarieren, aber in den Child-Klassen definieren. So kann eine Funktion je nach Kind verschiedenen Inhalt haben. Man kann den Inhalt von Funktionen auch erweitern.

`.hashCode()` gibt eine ID, die für jede Instanz individuell ist.