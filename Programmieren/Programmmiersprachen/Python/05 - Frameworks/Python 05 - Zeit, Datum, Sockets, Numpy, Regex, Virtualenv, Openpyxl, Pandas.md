# Zeit und Datum
## Standarts
### Unix
Unix zählt seit dem 01.01.1970 in Sekunden hoch. Jedes Computersystem nutzt diese Zeit und kann diese dementsprechend bei der Kommunikation mit anderen PCs nutzen.
### Standart Datum- und Zeitangaben  (ISO-Format)
YYYY-MM-DD HH:MM:SS -> 2024-09-17 09:26:31
## Datetime in Python
Um mit Zeit zu arbeiten, muss man das Modul "Datetime" verwenden.

```python
from datetime import date, time, datetime
my_date = date(year=2024, month=1, day=31)
my_time = time(hour=1, minute=14, second=12)
my_datetime = datetime(year=2024, month=7, day=22, hour=22, minute=12, second=55)
my_datetime = datetime(2024, 1, 5, 2, 4, 3)
```
### String to Date
```python
# Nur mit Bindestrichen oder als Zifferkette möglich
my_date = date.fromisoformat("2020-04-30)
my_date = date.fromisoformat("20200430)	 
```
### Schlecht formatierte Strings fixen
```python
# Anders formatierte Daten können folgendermassen konvertiert werden
# Der format_string beschreibt, wie der date_string formatiert ist
date_string = "01-31-2020 14:25:46"
format_string = "%m-%d-%Y %H:%M:%S"
my_datetime = datetime.strptime(date_string, format_string)
```
## Zeitzonen
Zeitzonen werden mit dem Modul Dateutil verwendet.
```python
from dateutil import tz
from datetime import datetime

# Find local London time
London_tz = tz.gettz("Europe/London")
now = datetime.now(tz=London_tz)
print(now)

# Find local time in Bern
now = datetime.now(tz=tz.tzlocal())
print(now)
```
### Zeitzonen konvertieren
```python
from dateutil import tz
from datetime import datetime

# Get local datetime
now = datetime.now(tz=tz.tzlocal())

# Get London time zone
London_tz = tz.gettz("Europe/London")

# Convert from local to London timezone
now_london = now.astimezone(London_tz)
```
## Mit Zeit rechnen
Mit `timedelta` kann man mit Zeit und Datum rechnen.
```python
from datetime import datetime, timedelta

now = datetime.now()
tomorrow = now + timedelta(days=1)
```
# Sockets
Sockets sind da, um Pakete über das Netzwerk zu übertragen.

Im Kurs hat es nur zwei kurze Beispiele gegeben, die einen Server und einen Client darstellen. Um mehr zur Netzwerkprogrammierung zu erfahren, sollte man sich [hier](https://realpython.com/python-sockets) informieren (von Kursleiter empfohlen).

## Echo-Server
```python
import socket

# Standart localhost Adresse
HOST = "127.0.0.1"

# Post to listen on (non-privilaged/usable ports are > 1023)
PORT = 65432

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
	s.bind((HOST, PORT))
	s.listen()

	# Verbindung entgegen nehmen
	conn, addr = s.accept()

	with conn:
		print(f"Connected by {addr}")
		while True:
			data = conn.recv(1024)
			if not data:
				break
			conn.sendall(data)
```

## Echo-Client
```python
import socket

HOST = "127.0.0.1"
PORT = 65432

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
	# Löst beim Server-Code das "accept" aus
	s.connect((HOST, PORT))
	s.sendall(b"Hello, world")
	
	data = s.recv(1024)

print("Received", repr(data))
```
# NumPy
NumPy bietet viele mathematische Funktionen. Am wichtigsten sind wohl Arrays, weshalb sich die Infos in diesem Kapitel besonders darauf beziehen.
## Arrays erstellen
```python
import numpy as np

# Einfaches Array
my_array = np.array([12, 42, 6, 2, 8, 23, 75, 7, 34, 74,])

# Mehrdimensionales Array
my_avenger_level_array = np.array([[1, 5, 7], [1, 6, 23]])

# Auf mehrdimensionale Arrays zugreifen
print(my_avenger_level_array[0, 3])
```
## Array-Funktionen
- `my_array.ndim` -> Gibt die Anzahl Dimensionen zurück
- `my_array.size`-> Gibt die Anzahl Elemente zurück
- `my_array.dtype`-> Gibt den im Array gespeicherten Datentypen zurück
- `my_array.dtype.name` -> Gibt den im Array gespeicherten Datentypen lesbarer zurück
- `my_array.copy` -> Kopiert ein Array
- `my_array.view`-> Klont das Array. Wird das geklonte Array verändert, ist auch das Original verändert. Denn die beiden haben einen Pointer zum selben Objekt.
## Slicing
Man kann Numpy-Arrays genau so slicen wie normale Arrays.
- `my_array[von:bis:schrittgrösse]`
Hat das Array mehrere Dimensionen, muss man folgendermassen slicen
- `my_array[von:bis:schrittgrösse, von:bis:schrittgrösse]` -> bei einem 2-Dimensionalem Array

```python
import numpy as np

# Konvertieren der Datentypen
# folgendes Beispiel konvertiert zu standart-integer 
my_array.astype(int)

# Speichern und laden (binäre Daten werden gespeichert)
np.save("DATEINAME", my_array)
np.load("DATEINAME.npy")

# Speichern und laden (Textdatei)
np.loadtxt("myfile.txt")
np.genfromtxt("myfile.csv", delimiter=",")
np.savetxt("myarray.txt", my_array, delimiter=" ")
```
# Regex
## Methoden
### Match
`re.match(pattern, string)`testet, ob der reguläre Ausdruck pattern am Anfang der Zeichenkette

## Character Classes
- `\w` Entspricht alphanumerischen Character, a-z, A-Z, 

## Special Characters
:,(

# Virtualenv
Das Python Virtual Environment ermöglicht das enkapsulieren von Projekten und deren Abhängigkeiten. Anstatt auf dem PC tausende Packages installiert zu haben, hat man dann für jedes seiner Projekte die paar Packages, welche dafür benötigt werden.
# Openpyxl
Ein Modul um Excel-Dateien zu bearbeiten und einzulesen. Die unten aufgelisteten Methoden sind nur ein kleiner Teil aller Helfermethoden. Man kann also fast alle Tabellen-Operationen direkt mit einer eingebauten Funktion umsetzen.
```python
from openpyxl import Workbook

# ein Workbook erstellen
wb = Workbook()
# Worksheet aktivieren
# In wb gibt es ein Worksheet per Default
w1 = wb.active 
# Titel des Worksheets ändern
w1.title = "New Title"
# Mehrere Worksheets in einem Workbook möglich
# 'mysheet' ist der Titel des neuen Worksheets w2
w2 = wb.create_sheet("mysheet")

# Werte setzen
w1["B5"] = 2
w1["A4"] = 2
w1.cell(row=42, column=12, value=1)

# Slicing
w1["A1":"B3"]

# speichern
wb.save("DATEINAME.xlsx")

# Einlesen
from openpyxl import load_workbook
wb = load_workbook("DATEINAME.xlsx")
```
# Pandas
Pandas ist ein Modul, mit dem man grosse Datenmengen verarbeiten kann.
Es ist vieeel besser als Openpyxl, da sehr perfomant und Dateiunabhängig. 
Es basiert auf Numpy und kann die Grafikkarte des PCs für tolle  Performance brauchen!
Pandas unterstützt 2D und 1D-Arrays.

```python
import pandas as pd

# Daten als DataFrame (2D-Array)
# wie eine Matrix
df = pd.DataFrame(data) 

# Beispiel
df = pd.DataFrame(np.random.randn(100,5), columns = list("ABCDE"))

# Daten als Series (1D-Array)
s = pd.Series(data)

# Beispiel
# Mit index kann man den Zeilenindex umbenennen. Ist eigentlich nicht notwendig.
s = pd.Series([5,10,15,20], index=["a", "b", "c", "d"])

# Fortgeschrittenes Beispiel eines DataFrames UNFERTIG
# --- UNFERTIG
data = {"Country": ["Belgium", "India", "Brazil"],
	   "Capital": ["Brussels", "New Delhi", "Brasilia"],
	   }

# Auf Daten zugreifen

# 1D-Array
df.loc[1]

# 2D-Array
df.loc[[2, 4]]

# Printen
df.to_string()

# Daten einlesen

# csv und json
df = pd.read_csv("data.csv")
df = pd.read_json("data.json")

# Excel
df = pf.read_excel("file.xlsx")
df.to_excel("myDataframe.xlsx", sheet_name="MySheetName")


# Hilfreiche Funktionen

# Nach fehlenden Werten suchen
# Gibt jeden Ort zurück, an dem nichts eingetragen ist
df.isnull()

# Zeilen mit mindestens einem Null value entfernen
df.dropna()

# Fehlende Werte (Null value) mit etwas auffüllen
# Das Beispiel füllt die Werte mit dem Wert '0' aus
df.fillna(0)

#Andere Varianten
af.interpolate()
df.replace()

# Iterieren über Zeilen
for i, j in df.iterrows():
	print(i, j)

# Entfernen von Werten
# Gibt ein neues Objekt ohne die entferne Werte zurück
df.drop(["a", "c"])

# Sortieren
df.sort_index()
df.sort_values(by="Country")
df.rank()

# Direkt Werte auslesen
df["b"]

# Boolean Indexing
# Nur die Werte, die über 1 sind
df[(df > 1)]

# Informationen über Daten sammeln
# Anzahl der gespeicherten Werte pro Dimension
df.shape()
#Namen der Spalten
df.index()
# Zählt die Menge an eingetragenen Daten pro Spalte
df.count()

# Summary
# Summe der Werte
df.sum()
# Kumulative Summe aller Werte
df.cumsum()
df.min()
df.max()
df.describe()

# Lambdas auf Werte im DataFrame anwenden
f = lambda x: x**2
df.apply(f)

# Die ersten 5 Werte ausgeben
df.head()

# Die letzten 5 Werte ausgeben
df.tail()
```

# Jupyter Notebook
Mit Jupyter kann man ein Markdown-Dokument mit einem Python-Skript verbinden. Dadurch ist es einfach, Beispiele, Aufgaben oder Notizen zu erstellen.