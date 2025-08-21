# Services & Dependency Injection
Eine Abhängigkeit (Dependency) ist ein Objekt, das von einem anderen Objekt benötigt wird.
Zum Beispiel ist ein 'Auto' von der Klasse 'Motor' abhängig, um zu funktionieren.
## Probleme mit Abhängigkeiten 
Wenn die Klasse 'Auto' den 'Motor' instantiiert, führt das zu folgenden Problemen:
- Will man die Klasse 'Motor' verändern oder ersetzen, muss man auch die Klasse 'Auto' verändern
- Wenn die Klasse 'Motor' auch Abhängigkeiten hat, müssen diese von der Klasse 'Auto' konfiguriert werden. Hätte man zb. die Klassen 'Flugzeug', 'Schiff' und 'Auto', die 'Motor' implementieren, müsste man die Konfiguration in all diesen Klassen separat durchführen. (The configuration of the dependency becomes scattered across the application.)
- Unit Tests werden durch Abhängigkeiten erschwert.
## Wie Dependency Injection diese Probleme löst
- Die Abhängigkeit durch Interfaces und Base-Klassen weg abstrahieren
- Die Abhängigkeit in einem Service Container registrieren. Services werden normalerweise in der Datei 'program.cs' registriert.
- Der Service wird dann in den Konstruktor injected, in welchem er gebraucht wird. Im Hintergrund wird automatisch eine neue Instanz erstellt.
## Was ist ein Service
Ein Service ist...
- Ein Objekt, das anderen Objekten einen Service (Dienst) zu Verfügung stellt (wie 'Motor' dem 'Schiff' oder 'Auto')
- Nicht unbedingt ein Web Service (kann aber einer sein)
## Design-Guidelines für Services
- Statische Klassen und Member vermeiden. Globalen State wenn nötig mit singleton Services umsetzen.
- Direkte Instantiierung von Abhängigkeiten vermeiden. Diese koppelt die Klasse an eine Bestimmte Implementierung der Abhängigkeit.
- Services sollten klein und selbsterklärend sein.
