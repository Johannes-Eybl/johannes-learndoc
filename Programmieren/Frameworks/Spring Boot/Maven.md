#springBoot #backend #java 
Maven ist ein Tool, welches zum Managen von Projekten verwendet wird. Am häufigsten wird es gebraucht, um build-Management und das Management von Dependencies zu übernehmen.
# Welche Probleme löst Maven?
Bei der Entwicklung eines Java-Projekts werden einige JAR-Files benötigt. Beispielsweise braucht man Spring, Hibernate, JSON und weitere.
Man kann diese JAR-Dateien einzeln herunterladen und manuell zum eigenen Projekt hinzufügen, doch das ist aufwendig.

Maven lädt diese JAR-Dateien von selbst herunter und fügt sie dem Projekt an. Man muss Maven die Dependencies mitteilen und sich sonst um nichts kümmern! 
Maven ist also wie ein Helfer, dem man eine Liste gibt, die es dann besorgt!
# Wie Maven funktioniert
1. Maven liest die Config-File, in der alle Dependencies, die es laden soll, aufgelistet sind.
2. Maven prüft in der lokalen Repo, ob die gewünschten Dateien bereits vorhanden sind.
3. Maven lädt die fehlenden Dateien aus dem Internet (Maven Central Repo) 
4. Maven speichert die runtergeladenen Dateien auf dem lokalen Repo.
5. Maven kann das Projekt nun builden und ausführen.
# Maven Projektstruktur
Maven hat eine standartisierte Projektstruktur:

![[MavenProjektstruktur.png]]

| Directory          | Beschreibung                                                             |
| ------------------ | ------------------------------------------------------------------------ |
| src/main/java      | Java Source Code                                                         |
| src/main/resources | Properties / config files die von der Applikation genutzt werden         |
| src/main/webapp    | JSP-Dateien, web-config-Dateien und andere Web-Assets (Bilder, CSS etc.) |
| src/test           | Testing Code                                                             |
| target             | Directory für kompilierten Code. Wird automatisch von Maven erstellt.    |
| pom.xml            | Project Object Model-Datei                                               |
# Schlüsselkonzepte
## POM-File
Die Project Object Model-Datei ist die Konfigurationsdatei für das Projekt