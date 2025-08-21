#programming 
#python 


# Error Handling
## Debugging-Tools
Python hat eine Debugging-Library, mit der man im Code mit dem `breakpoint()` selber Breakpoints setzten kann. 
Viel nützlicher ist aber der in VS-Code und PyCharm eingebaute debugger. Dieser hat genau die gleiche Funktionalität, ist aber viel einfacher zu bedienen.

## Error Handling im Code
Mit `try` und `except` kann man beim Programmablauf auftretende Fehler verarbeiten. 
```python
# Takes inputs and converts them to Integer until success
def takeInputUntilGottenAnInteger():
	try:
		return int(input("Your input (pls input a number): "))
	except:
		return takeInputUntilGottenAnInteger()
```

- Eigene Fehlermeldungen kann man erstellen, in dem man eine Klasse schreibt, die von der Klasse `exception` erbt
Neben den oben genannten Schlagwörtern gibt es auch noch andere, welche man fürs Error-Handling verwenden kann:
### Else
Bei einem Try-Catch Statement wird der Else-Block nur dann ausgelöst, wenn der Try-Block ohne Fehler ausgeführt wird.
```python
# Takes inputs and converts them to Integer until success
def takeInputUntilGottenAnInteger():
	x = 0
	try:
		x = int(input("Your input (pls input a number): "))
	except:
		return takeInputUntilGottenAnInteger()
	else:
		print("X will now be the inputted Number")
```
### Finally
Der Finally-Block wird in jedem Fall ausgeführt, auch wenn ein Error gethrowt wird und sogar wenn im Try ein Return-Statement ist.

# Module
Mit dem `import`-Statement kann man Module importieren. Das erlaubt einem die Nutzung von Methoden und Klassen, die zu diesen Modulen gehören.
```python
# Import module Math and use it with the name m
import math as m

# Import specifically the function pi from the Math Module
from math import pi

# Imports each Method from Math. Not recommendet as you should always import exactly what you need. Different Libraries can have the same Method names, this prevents corresponding Errors.
from math import *
```
- Es gibt sehr viele Module
# Daten lesen & schreiben
Mit `open(path, berechtigung)` öffnet man Dateien. Wenn der angegebene Pfad nicht zu einer Datei führt, wird an dieser Stelle einer erstellt.
***Achtung:*** Falls das File schon existiert und die Write-Berechtigung "w" genutzt wird, wird das File gelöscht und ein neues erstellt. 
```python
f = open("/myPath/myFile.txt", "r")
print(f.read())
f.close
```
- r  -> read
- w -> write. Überschreibt Dateien!!!
- a -> append. Erweitert Dateien
- r+ -> write & read

Die open-Funktion gibt die Datei zurück, man sollte also `f = open(path, mode)` schreiben.

Mit der `.write(string)`-Funktion kann man Text in einer Datei platzieren.
Mit `.close()` schließt und speichert man die Datei wieder. Das ist umbedingt notwendig, wenn man nicht mit `with open() as ...:` arbeitet!

Die folgende Notation ist die übliche Weise, Dateien zu verwenden und schließt die Datei danach automatisch.
```python
with open("datei.txt", "w") as f:
	f.write("Mein String. Hallo Welt.")
```
# JSON
JSON steht für JavaScript Object Notation. Es ist ein viel verwendetes Dateiformat.

Wenn man mit JSON arbeiten will, muss man mit dem entsprechenden Modul arbeiten. 
Also `import json`.
## String & Files to Dict
Mit `json.loads(string)` kann man einen JSON-String zum Dict machen.
Mit `json.load(file)` kann man JSON-Files direkt  zum Dict machen
```python
# Converts a JSON-Formatted String to obj
with open("myJsonFile.json", "r") as file:
	obj = json.loads(file.read())

# Converts a JSON-Formatted file to obj
with open("myJsonFile.json", "r") as file:
	obj = json.load(file)
```
## Dict to JSON
```python
import json

myDict = {
	  "titel": "Der Python Kurs",
	  "autor": "thomas"
}

# This converts a dict into a JSON-formatted string
json_string = json.dumps(myDict)

# This writes a dict directly to a JSON file
json.dump(myDict, open(filePath, "w"))
```
# CSV
Excel-Daten können als .csv-Dateien abgespeichert werden. Diese können mit dem csv-Modul eingelesen werden.
```python
import csv
with open(myFile.csv) as csv_file:
	csv_reader_object = csv.DictReader(csv_file, delimiter=",")
	
	for row in csv_reader_object: # loop over list / entries in csv
	# each row will be a dictionary with each column name as Key
		print(row)
```
# XML
Um XML-Dateien zu schreiben, muss man das 'ElementTree'-Modul verwenden.
```python
import xml.etree.ElementTree as ET

file1 = '''
	<foo>
		<bar>
			<type foobar="Hello"/>
			<type foobar="Hello"/>
		</bar>
	</foo>
'''
tree = ET.fromstring(file1)

# no support for multiple queries
x = tree.findall("bar/type")

for item in x:
	print(item.get("foobar"))
	
```
