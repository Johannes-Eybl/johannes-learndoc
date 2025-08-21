#programming 
#python 

# Einleitung
Python wurde von Guido van Rossum erfunden und ist älter als Java!
## Wichtigste Eigenschaften
Python ist...
- ...dynamisch. Siehe [[Dynamic Typing]], [[Duck-Typing]]
- ...interpretiert. Siehe [[Kompilierte Sprachen, Interpretierte Sprachen]]
- ...eine Sprache, die [[OOP]], aber auch funktionales, aspektorientiertes (?) und strukturiertes Programmieren unterstützt.
- ...implementiert Speicherfreigabe durch Referenzzählung

## Warum Python genutzt wird
Python setzt sich wegen folgenden Eigenschaften von anderen Programmiersprachen ab:
- Lesbarkeit
- Relativ kurze Programme
- Direkte Tests weil ohne Compiler
- Viele Bibliotheken

## Usecases
- Webdev (mit Flask oder Django)
	- Python wird von Instagram, Uber, Reddit, Spotify und vielen anderen genutzt.
- Data Science (mit NumPy, SciPy oder Pandas)
- AI (PyTorch, TensorFlow, OpenCV, Keras)
- Quantum Computing
- Embedded Boards (CircuitPython, MicroPython)


# Eigenständige Python-Skripts (Shebang)
Ein eigenständiges Skript kann auch ohne die Angabe der python-Version in der Kommandozeile gestartet werden. Man kann das Skript so also wie einen Befehl verwenden!

In dem man am Anfang des Skripts `#!/usr/bin/env python 3` angibt, Beziehungsweise den Pfad zur eigenen Python-Executable (dem Speicherort).

# Docstrings
Docstrings werden dazu verwendet, Funktionen für die Dokumentation zu beschreiben. Mit Annotationen (Wie in Spring Boot mit dem @-Symbol) kann man eine Beschreibung, Parameter und den Rückgabewert definieren.
```python
def func(x):
	""" Das ist ein Docstring """
	return x * x
```

Mit `print(func.__doc__)` kann man auf den Docstring zugreifen.

# Naming-Conventions
- Package: kleingeschrieben (package, mypackage)
- Module: Klein mit Underscore
- Funktionen: kleingeschrieben mit underscore (funk, my_funk)
- Variablen: kleingeschrieben mit Underscore (x, var, meine_var)
- Klassen: CamelCase (MyClass, Model)
- Methoden: kleingeschrieben mit Underscore (class_method, method)
- Exception Names: CamelCase (HTTPServerError) → Exceptions sind auch Klassen
- Konstanten: gross mit Underscore (MEINE_KONSTANTE)

# Rechenoperationen
Wie auch in C# oder Java lassen sich Rechenoperationen in Python direkt in der Definition durchführen lassen (zB. `x += 5`). So wird Arbeitsspeicher gespart.

- Grundoperationen: +, -, *, /
- Gruppierung: ()
- Potenz: **
- Floor division: //
- Modulo: %
# Variablen
## Variable-Typen auslesen
Mit `type(var)`kann man den Typen einer Variable auslesen. Dieser wird zur Runtime automatisch bestimmt ([[Dynamic Typing]]).

## Variablen zuweisen
Das Zuweisen von Variablen funktioniert in Python so wie in jeder anderen Sprache.
Eine Besonderheit ist, dass man mehrere Variablen in einer einzigen Zeile definieren kann: `a, b, c = 1, 2, 3` ist legaler Python-Code.

## Variablen löschen
Mit `del(var)`kann man eine Variable aus dem RAM löschen.

# Datentypen
Jeder Datentyp hat eigene eingebaute Funktionen. Beispielsweise kann man Integers mit der `hex(var)`-Funktion zur Hexadezimalzahl umwandeln. Diese sind hier aber nicht aufgelistet.
## None / NoneType
`None`beschreibt die Abwesenheit eines Werts. Entspricht `null`in anderen Programmiersprachen.
## Nummern
- bool (true, false)
- int (beliebig grosse ganze Zahlen)
- float (beliebig genaue Zahlen)
	- Achtung! Anfällig auf Rundungsfehler. Nie zwei errechnete Floats auf Gleichheit prüfen! Stattdessen immer mit Differenz arbeiten.
- complex (komplexe Zahlen) -> zB. `1 + 6j`

## Strings
- Werden als Zeichenkette gespeichert
- Lassen sich addieren
- Mehrzeilige Strings lassen sich mit drei Anführungszeichen schreiben
## Listen
```python
myList = ["a", "b", "c"]
```
- Sind veränderbar
- Zugriff von [0] bis [n-1]
- Rückwärts-Zugriff von [-1] bis [-n]
#### Listen erweitern
Neue Werte kann man einer Liste mit folgenden Möglichkeiten zuweisen:
- `+`
- `+=`
- `[-1]`
- `.append(var)` 
- `.add(var)`
- `.add(var)` 
#### Listen verkleinern, Elemente entfernen
- `.pop(index)` -> Entfernt ein Element an dem Index, der angegeben wird. Retourniert das entfernte Element
- `.remove(element)` -> nimmt ein Element als Parameter und entfernt dieses von der Liste. Entfernt nur das erste Vorkommen dieses Elements in der Liste
#### Weitere Listenfunktionen
- `.reverse()` -> kehrt Listen um.
- `.copy()` -> kopiert
- `.extend()` -> packt listen von listen aus
- `.count()` -> zählt Elemente
- `.index()` -> nimmt als Parameter einen Wert und gibt dessen Position bzw. Index zurück. Gibt den Index des ersten Vorkommens dieses Wertes zurück.
- `.insert()` -> Insertet
- `.sort()`  -> sortiert Elemente in dieser Liste. Mit `.sort(reverse=true)` kann man umgekehrt sortieren, also absteigend.
## Tuple
``` python
myTuple = ("a", "b", "c")
myFirstTupleElement = myTuple[0]
```
- Tuples sind unveränderbare Listen
- Nur auslesen von Daten ist erlaubt
- Benötigen weniger Speicher als Listen

***ABER*** man kann Tuples mit `+=` erweitern. Wenn man das verwendet, wird das Tupel ausgelesen, ein neues Tuple mit dem neuen Content erstellt und dieses dann dem alten Tuple zugewiesen.

## Set & FrozenSet
```python
mySet = {"a", "b", "c"}
# oder
mySet = set(["a", "b"])

mySet.Add("e")
```
Im Set gibt es jedes Element **nur ein Mal**. Es ist eine *ungeordnete* Sammlung von Elementen ohne Duplikate. Es gibt:
- Set -> Veränderbar
- Frozenset -> Nicht veränderbar
## Map / Dict
Eine Map besteht aus einer beliebigen Anzahl von Key-Value-Paaren. 
```python
mydict = {"Milch": "milk", "Ei": "egg", "Mehl": "flour"}`
```
Man kann eine Map zB. auf folgende Weise verwenden:
`if 'Milch' in myMap:`

# Kontrollstrukturen

## While Schleife
```jsx
x = 1
while x < 10:
	print("Hallo")
	x += 1
```
## For Schleife
```python
for x in range(1, 10):
	print("Hallo")

#oder

myList = ["a", "b", "c"]
for element in myList:
	print(element)
```
- Startwert optional
- Schrittgrösse kann als dritten `range()`-Parameter mitgegeben werden
### Range()
Mit Range kann man das Verhalten eines Loops genau definieren.
```python
for x in range(a, b, c):
	#doSmth
```
- a -> Der Startwert
- b -> Der Endwert. Nicht inklusive.
- c -> Schrittgrösse. Standardmäßig 1.
## Break and Continue

- Break unterbricht einen Loop
- Continue springt im Loop nach oben, also zur nächsten Schleife / nächsten Iteration. Der restliche Code der aktuellen Schleife wird ignoriert.

# Funktionen
Funktionen verhindern sich wiederholenden Code. Sie können lokale Variablen enthalten.
```python
def bisX(x):
	for i in range(0, x):
		print(i)
```

- Mit einem ‘default’-Wert kann man Funktionen einen default parameter Wert geben. Bei mehreren Parametern müssen die mit einem default zuhinterst aufgeschrieben werden.
    `def func(x=1):`

- Mit einer Angabe vor dem Parameter kann man diesem einen zu erwartenden Datentypen geben.
	`def func(int x):`

- Mit einem Pfeil zu einem Datentypen hinter den Parametern kann man den Rückgabetypen festlegen
	 `def func() -> int:`

- Man kann auch eine beliebige Anzahl an Parametern erlauben:
		```python
		def func(*args)
		```
## Beliebige Parameter

## *
Man kann einer Funktion eine beliebige Anzahl an Parametern erlauben. Das macht man mit einem Sternchen
```python
def myfunction(*args):`
	for arg in args:
		#dostuff

myfunction("eins", "zwei")
```
Dann kann man über die liste (!) der args drüber loopen (for arg in args)

## **
Wenn man bei `args` zwei Sternchen verwendet, wird anstatt einer Liste ein Dict generiert
```python
def fun(**args):
	for k, v in args.items():
		print(k, v)

fun(erster="Eins", zweiter="Zwei", dritter="Drei")
```
## Rekursion
Rekursive Funktionen sind Funktionen, die sich selbst aufrufen. Man muss bei der Programmierung gut aufpassen, dass keine unendliche Schleife entsteht.

Das Gegenstück zur rekursiven Methodik ist die iterative Methodik (loops).

### Abbruchbedingung
Eine rekursive Funktion braucht eine Bedingung, bei der sie sich nicht mehr selbst aufruft. Diese Bedingung nennt man auch einen _Rekursionsanker_.

### Beispiel
```python
def factorial(n):
	if n == 1:
		return 1
	else:
		return n * factorial(n-1)
```


