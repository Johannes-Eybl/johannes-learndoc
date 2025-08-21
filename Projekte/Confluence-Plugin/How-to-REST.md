Folgende Schritte werden benötigt um ein REST-Plugin zu erstellen:
# 1. Plugin-Projekt erstellen
Der Befehl `atlas-create-refapp-plugin` erstellt eine Plugin-Vorlage.

| group-id    | com.atlassian.plugins.tutorial |
| ----------- | ------------------------------ |
| artifact-id | name des rest-links            |
| version     | 1.0                            |
| package     | com.atlassian.plugins.tutorial |
# 2. Rest-Modul hinzufügen
Innerhalb des im Schritt 1 erstellten Ordners den Befehl `atlas-create-refapp-plugin-module` ausführen. Nummer 7, REST Module Plugin, auswählen. 

| Classname    | MyRestResource                      |
| ------------ | ----------------------------------- |
| Package Name | com.atlassian.plugins.tutorial.rest |
| REST path    | /myrestresource                     |
| Version      | 1.0                                 |
# 3. Plugin compilen
Mit dem Befehl `atlas-run` werden alle Dependencies runter geladen und das Plugin compiled. Danach ist es unter `hostname:port/rest/myrestresource/1.0/message` verfügbar.