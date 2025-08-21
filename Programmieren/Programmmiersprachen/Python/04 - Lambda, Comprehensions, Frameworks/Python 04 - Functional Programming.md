#programming 
#python 
# Lambda
Lambda definiert kurze Funktionen, deren Rumpf durch einen Ausdruck gegeben ist. 
Vor dem Doppelpunkt werden die Parameter definiert und nach dem Doppelpunkt ist der Funktionskörper.
Man kann Lambdas auch als Variablen speichern.
```python
# Definieren in einer Variable
meinLambda = lambda x,y: x*y

# Auslösen der Funktion. Ihr Name ist nun der Name der Variable
meinLambda(2,3)

# Mit dieser Schreibweise kann man die Lambda-Funktion direkt ausführen
(lambda x,y: x*y)(2,3)
```
## Warum Lambda
- Verwendung als Argumente für Funktionen
- Argument-Funktionen werden of nur ein mal verwendet und kurz, sodass sich ein Name nicht lohnt
- Funktions-Fabriken (Funktion als Rückgabe einer Funktion)
- Ergebnisfunktion kann durch Lambda-Ausdrücke gefiltert werden (?)
```python
# Fortgeschrittene Lambda-Nutzung
def gen_adder(c):
	retund lambda x: x + c

# add5 ist nun eine Funktion die X nimmt und X+5 zurück gibt
add5 = gen_adder(5)
```
# Map
```python
list(map(lambda x: x-5, range(10)))

```
# Filter
Filtert alle nicht passende Objekte aus. Filter ist eine Funktion mit zwei Parametern: ein Lambda und ein iterierbares Objekt. 
```python
list(filter(lambda: x: x > 2, [3, -2, -1, 1, 99]))

# returned [3, 99]
```
# Partial
Mit Partial kann man bei einer Funktion deren Argumenten einen Standartwert geben, damit man diesen nicht jedes mal ausfüllen muss. Dieser Wert ist dann fixiert und muss nicht mehr eingegeben werden.
```python
from functools import partial

# Einen Binären Wert zu einem Int umwandeln
int("10011", base=2)

int2 = partial(int, base=2)
int2("1001") # Wandelt einen Binären Wert zu einem Int um
```
# Reduce
Reduktion eines iterierbaren Objekts auf ein Element.
Es gibt immer zwei Werte. Den Akkumulator und die current value Der Akkumulator ist von iteration zu iteration immer dasselbe Objekt, welches nach und nach bearbeitet / berechnet wird. Die current value ist ein mal jedes Objekt in der Liste, über die Iteriert wird (wie bei einem for loop).
```python
from functools import reduce

reduce(lambda x, y: x*y, range(1,5)) # gibt 24 aus

```
Reduce ist folgendermassen aufgebaut: `reduce(eineFunktion, eineListeOderRange, einStartwert`
# List comprehensions
- Ermöglicht die deklarative und kompakte Schreibweise von Listen
- Stammt von der funktionalen Programmiersprache Haskell

Eine List comprehension besteht aus einer Ausgabe (pro iteration des Loops wird ein Wert ausgegeben), einem Loop und einer Bedingung. 

### Vergleich List-Comprehension mit Map&Filter
`[str(x) for x in range(10) if x % 2 == 0] -> ["0", "2", "4", "6", "8"]`
ist gleich wie
`list(map(lambda x: str(x), filter(lambda x: x % 2 == 0, range(10))))`
Die List Comprehension ist deutlich simpler.
```python
# Summe aller Zahlen bis 10
sum(x for x in range(10))
```
### Syntax
`[expression for pat in sequence if condition]` 
bzw.
`[expression for pat1 in sequence1 if condition1
		`for pat 2 in seq2 if cond2
		`for pat3 in seq3 if cond3]`
Man darf nicht vergessen, dass man auch mehrere Loops innerhalb der Comprehension verwenden kann.

### Beispiel anhand einer Übung
``` python
# Erstelle das kartesische Produkt aus [0, 1, 2] und ["a", "b", "c"] mittels list comprehensions
# [[0, a], [0, b], [0, c], [1, a], [1, b], [1, c], [2, a], [2, b], [2, c]]

numberList = [0, 1, 2]
charList = ["a", "b", "c"]

# Hier werden 2 Loops verwendet
myNewCarthesianProduct = [[number, char] for number in numberList
												for char in charList]
```
# Dict Comprehensions
Mit der Dict-Comprehension kann man mit einem iterierbaren Objekt ein neues Dictionary erstellen. Es muss am Anfang die Variable für den Schlüssel und den Wert gesetzt werden, damit ein Dict erstellt wird. Der Rest ist praktisch wie eine List-Comprehension.
```python
# Syntax
{<new_key>:<new_value> for <item> in <iterable> if condition}

# Define dict
dict1 = {"a": 1, "b": 2, "c": 3}

# Double dict values
double_dict1 = {k:v*2 for (k,v) in dict1.items()}

# Result
{"a": 2, "b": 4, "c": 6}
```
