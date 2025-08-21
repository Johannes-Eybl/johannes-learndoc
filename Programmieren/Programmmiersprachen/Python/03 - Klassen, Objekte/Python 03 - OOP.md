#programming 
#python 
# Objektorientierung
[OOP bricht ein Problem in mehrere kleinere Dinge (Objekte) auf.  Der Zustand eines Programmes wird  in diesen Objekten gespeichert. ](OOP.md)
# Alles sind Objekte
Alle Werte in Python sind in Wirklichkeit auch Objekte. Denn sie sind nicht reine Daten, sondern haben assoziierte Attribute und Methoden, auf welche zugegriffen werden kann. 

Jedes Objekt, und somit auch jeder Wert in Python, hat folgende Eigenschaften:
- Identity -> Die Adresse im Speicher
- Type -> Die Art von Objekt
- Value -> Der Wert, den das Objekt speichert. Die Liste `[1, 2]` hat die Werte 1 und 2.
# Objekte vergleichen
## Identität -> is & is not
Jedes Objekt hat eine Identität, welche mit den `is` und `is not`-Operatoren verglichen werden kann. Diese Operatoren prüfen, ob zwei Variablen am selben Ort gespeichert sind.
Achtung - Zwei mal dasselbe Objekt zu erstellen macht diese Objekte nicht gleich. Man muss ein Objekt 'direkt' kopieren, damit man es mit dem `is` Operator vergleichen kann.
```python
# Bei zwei gleich erstellten Listen gibt `is` ein `false` aus
x = ["a", "b", "c"]
y = ["a", "b", "c"]

x is y -> false

# Setzt man eine Variable zum Wert einer anderen, gibt der Vergleich `true`aus.
z = y
y is z -> true

# `y` und `z` haben eine Referenz zum selben Ort im Speicher. Verändert man das eine, wird auch das andere Verändert, denn sie sind dasselbe Objekt.
z.append("d")

print(z) -> ["a", "b", "c", "d"]
print(y) -> ["a", "b", "c", "d"]
```
## Gleichheit -> ==
Wenn man Variablen auf Gleichheit überprüft, wird nur deren Inhalt getestet. Im Gegensatz zum Identitätstest können die Werte an zwei unterschiedlichen Stellen gespeichert sein.
```python
# Bei zwei gleich erstellten Listen gibt `==` ein `true` aus
x = ["a", "b", "c"]
y = ["a", "b", "c"]

x == y -> true
```
Wenn man zwei Objekte vergleichen will, muss man immer `==`verwenden. Ausgenommen ist der Vergleich mit `none`, bei dem man mit `is` und `is not` arbeitet.
# Klassen definieren
```python
class Box:
	# Klassenvariable mit default-Werte
	h = 0
	w = 0
	d = 0

	# `self` anstatt `this`
	def getvolume(self):
		return self.w*self.h*self.d

# Setzen von Klassenvariablen
Box.h = 4

# Instantiieren einer neuen Box
b = Box()

# Setzen von Instanzvariablen
b.h = 5
```
# Access Modifiers
In Java sind Access Modifiers `private`, `public` etc. In Python werden diese Modifier mit Unterstrichen definiert. 
- public -> kein Prefix
- protected -> _
- private -> __
```python
class Test:
	def _protected_method():
		pass

	def __private_method():
		pass
```
# Konstruktor / Initializer
Die `__init__()`-Methode fungiert als ein Konstruktor für alle Klassen in Python. Es sorgt dafür, dass bestimmte Werte (Instanzvariablen) beim Initialisieren mitgegeben werden müssen.
```python
class Box:
	# Die Instanzvariablen müssen nicht seperat aufgeführt werden!
	def __init__(self, height, width, depth):
		self.height = height
		self.width = width
		self.depth = depth

b = Box(1,2,3)
	
```
# Klassen- vs Instanzvariablen
## Instanzvariablen
- Wert von Objekt zu Objekt unterschiedlich
- Nicht durch Objekte geteilt, jedes Objekt hat eine eigene Kopie der Variable
- Aufruf über `self`
## Klassenvariablen
- Innerhalb der Klasse deklariert, aber außerhalb der Instanzmethoden oder des Konstruktors
- Geteilt durch alle Objekte. Sie alle haben eine Referenz zum selben Wert.
- Aufruf über `Klassenname.Variablename`
# Magic Methods / Dunders
Dunders sind Methoden, die jedes Objekt von sich aus besitzt. So wie in Godot fast jede Node von der Grundklasse "Node" erbt und deren Methoden bekommt, hat in Python jede Klasse/jedes Objekt diese Dunder-Methoden
Diese Methoden kann man in der eigenen Klasse auch Überschreiben. [Hier](https://www.geeksforgeeks.org/dunder-magic-methods-python/) befindet sich eine Liste dieser Methoden. 

- `__str__` -> definiert eine Funktion, die das Objekt in einen String umwandelt. Es soll eine für menschen lesbare Beschreibung sein.
- `__repr__` -> Gibt einen String zurück, mit dem man mit `eval` ein neues Objekt erstellen kann. Also `Person("Hannes", 23, "Bern")`. Er soll so formatiert sein, dass das Erstellen von einem neuen Objekt direkt möglich ist.
- `__eq__`-> vergleich zwei Objekte des gleichen Typs

# Dataclass
Ein einfacherer Weg, kleine Klassen zu erstellen, ist die Dataclass. Diese hat mehrere Variablen aufgelistet und generiert im Hintergrund automatisch einen Konstruktor.
```python
from dataclasses import dataclass

@dataclass
class Car:
	name: str
	# Man kann Werten auch ein Default geben
	wheels: int = 4

c = Car("Mercedes", 4)
```
Der Dataclass-Annotation kann man verschiedene optionale Werte mitgeben. Hier sind nur zwei von vielen aufgelistet
- Mit `@dataclass(frozen=true)` kann man diese frozen/immutable machen
- Mit `@dataclass(order=true)` kann man die Werte in einer Dataclass sortieren

Dataclasses generieren verschiedene Funktionen automatisch:
- `__init__`
- `__eq__` -> Wird nur implementiert, wenn man `@dataclass(sortable = true)` schreibt.
- `__repl__`
# Vererbung
```python
# Grundklasse Animal
class Animal:
	eyes = 2
	def __init__(self):
		self.species = "mammal"

# Erbt 'eyes' und 'species'
class Dog(Animal):
	fur_color = "black"
	def __init__(self):
		self.name = "D"
		# Der Konstruktor der Klasse 'animal' muss hier aufgerufen werden, da ein anderer Konstruktor vorhanden ist
		super().__init__(self)

# my_dog hat eyes, species und fur_color
my_dog = Dog()
```
# Mutable und immutable
Immutable bedeutet, dass ein Wert nicht geändert werden kann, wenn er einmal kreiert wurde. "Readonly" in C# ist immutable

Mutability beschreibt wie sich Objekte verhalten, wenn sie verändert werden. Mutable Objekte können verändert werden, immutable Objekte können nicht verändert werden, wenn sie ein mal kreiert worden sind. Wird ein immutable Objekt doch verändert, wird ein neues erstellt. 
### Immutable Datentypen
- Numbers
- Bools
- Bytes
- Strings
- Tuples
- Frozen Sets
### Mutable Datentypen
- Lists
- Dicts / Maps
- Sets
## Mutable Objekte verändern
Wird ein mutables Objekt verändert, verändern sich auch alle Referenzen zu diesem Objekt. Die Speicheradresse bleibt also dieselbe.
## Immutable Objekte verändern
Wird ein immutable Objekt verändert, entsteht im Hintergrund ein neues Objekt. Der gleiche Variablenname bezieht sich also nun auf eine neue Speicheradresse.  
![[DifferencesBetweenMutableAndImmutableObject.png]]

[Quelle](https://medium.com/@codingwinner/understanding-mutable-and-immutable-in-python-code-step-by-step-5bdae89f4707)

# Mehrfache Vererbung
In Python kann von mehreren Klassen geerbt werden

```python
# Superclass
class Mammal:
	def mammal_info(self):
		print("Mammals give direct birth")

# Superclass
class WingedAnimal:
	def winged_animal_info(self):
		print("Winged animals can flap.")

# Subclass
class Bat(Mammal, WingedAnimal):
	def __init__(self):
		print(super().winged_animal_info())

# Can now call functions from both parent classes
my_bat = Bat()
my_bat.mammal_info()
my_bat.winged_animal_info()
```
# Auf vererbte Methoden und Felder zugreifen
Mit der `super()`-Methode kann man auf die Superklasse zugreifen -> `super().methode()` oder `super().variable`
# Viele Parameter (kwargs)
Wenn man mit einer grossen Menge von Parametern arbeitet, macht es Sinn, diese Parameter mit `**kwargs` weiter zu geben. `**kwargs` muss immer am Schluss der Parameter stehen! (`**kwargs`->Keyword Arguments)

Siehe mehr: 
[[Python 01 - Grundlagen#Beliebige Parameter]]
```python
class Sector3(Circle3):
	def __init__(self, angle, **kwargs):
		self.angle = angle
		super().__init__(**kwargs)
```