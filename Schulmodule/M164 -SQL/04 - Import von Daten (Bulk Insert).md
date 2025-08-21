#schule 
#m164

# Lernziele

- Sie können Daten aus verschiedenen Quellen importieren
- Sie kennen die Primär- und Fremdschlüsselproblematik beim Import und können dieses Problem lösen
- Sie können Daten aus bestehenden Trabellen in eine neue Tabelle überführen
- Sie können Daten aus einer betehenden Tabelle in neue Tabellen überführen

Dieser Abschnitt beschäftigt sich mit den Problemen, die beim Import von Daten enstehen können, sowie auch mit dem allgemeinen Import von Daten mit .csv-Dateien.

# Primärschlüsselproblematik

Wenn Daten importiert werden und das System die Primärschlüssel dieser Daten automatisch festlegt, kann nicht garantiert werden, dass die Primärschlüsselwerte der Daten mit denen der Originaldaten übereinstimmen!!!

# Fremdschlüsselproblematik

Die Fremdschlüsselproblematik entsteht aus der Primärschlüsselproblematik heraus.. Wenn beim Import von Datensätzen die Primärschlüsselwerte verfälscht worden sind, kann das zu falschen Verweisen bei den Fremschlüsselwerten führen.

# Lösung des Problems

Die meisten Datenbanken haben die Lösung zu diesem Problem bereits eingebaut und kann relativ einfach gelöst werden. Mit `insert` kann man Primärschlüsselwerte ohne weiteres in MariaDB und MySql importieren.

# Importieren von Daten (MariaDB)

Folgender Befehl importiert alle Daten der Datei in eine MariaDB-Datenbank

```sql
LOAD DATA LOCAL
	INFILE `C:\\Daten\\CSV\\Autoren.csv´
	INTO TABLE Autoren
	FIELDS ESSCAPED BY ´\\´
	TERMINATED BY ´;´
	LINES TERMINATED BY ´\r\n´
	IGNORE 1 LINES
	(ID, Nachname, Vorname, Adresse, Email, @OrtID)
	SET OrtID = NULLIF(@OrtID, "");

```

- `INFILE` → Verzeichnis und Name der zu importierenden Datei
- `LOCAL` → Dateien vom lokaeln Computer (Client) importieren
- `INTO TABLE` → Tabellenname
- `FIELDS ESCAPED BY` → Bei Sonderzeichen muss “\” direkr davor stehen
- `TERMINATED BY` → Zeichen, um die Attributwerte voneinander zu trennen
- `LINES TERMINATED BY` → Unter Windows erfolgt der Zeilenumbruch mmit Carriage Return und Line Feed
- `IGNORE 1 LINES` → Ab welcher Zeile die Daten beignnen (Ignoriere eine Zeile, die die Kopfzeile ist)
- Zeile mit Attributen → Welche Spaltenwerte in welches Attribut eingefüllt werden sollen (muss identisch sein mit der Reihenfolge der ..csv-Datei)
- `SET OrtID=NULLIF(@OrtID,"")` → Standartmässig werden fehlende Werte in .csv-Dateien als leere Strings importiert. Mit diesem Befehl kann man festlegen, dass ein leerer Strin als `null` importiert werden soll.

# Importieren von Daten (SQL Server)

Folgender Code importiert die Daten der Datei “Orte.csv” in die Tabelle “Orte”

```sql
BULK INSERT dbo.Orte
	FROM "C:\DAten\CSV\Orte.csv"
	WITH (
		CODEPAGE = "65001",
		FORMAT = "CSV"
		FIRSTROW = 2,
		FIELDTERMINATOR = ";",
		ROWTERMINATOR = "0x0a",
		KEEPIDENTIY,
		KEEPNULLS
);

```

- `FROM` → Verzeichnis und Name der zu importierenden Datei
- `CODEPAGE` → 65001 ist die Codepage für .csv-Dateien im UTF-8 Format
- `FORMAT` → Gibt an, welches Dateiformat die Datenquelle hat
- `FIRSTROW` → Ab welcher Zeile die Daten beginnen. (1. Zeile = Kopfzeile)
- `FIELDTERMINATOR` → Mit welchem Zeichen Werte voneinander getrennt werden
- `ROWTERMINATOR` → Hex-Wert für den Zeilenumbruch
- `KEEPIDENTITY` → Wenn Primärschlüssel importiert werden sollen und vom System verwaltet werden sollen, muss dieser Befehl genutzt werden
- `KEEPNULLS` → Fehlende Werte als `null` in die Tabelle importieren

# Import mit INSERT

Beispiel eines `INSERT`-Befehls:

```sql
INSERT INTO orte (id, plz, ort)
	VALUES (2, 2342, "Bitch"),
	(3, 1984, "Wow");
```

Wichtig:

- Man muss sich mit dem `USE <tabelle>` zuvor in die richtige Datenbank manövriert haben!
- Bei Sonderzeichen muss man normalerweise ein Backslash “\” nutzen
- Um Primärschlüsselwerte mit `AUTO INCREMENT` einzufügen, muss man den `SET IDENTITY_INSERT <tabellenname> ON`-Befehl verwenden. Dieser Wert muss nach dem Importieren von Daten wieder zurückgesetzt werden.