Liquibase ist ein Tool, mit dem man Datenbanken migrieren und Version Control einfacher durchführen kann. 
# Was macht Liquibase
- Änderungen in der Datenbank tracken (in yaml, json, xml oder sql)
- Migrationen automatisch anwenden. Liquibase prüft ob es Änderungen gibt und wendet sie automatisch an.
- Rollback support. Liquibase vereinfacht das Rollback von Datenbanken.
- Arbeit über Environments hinweg. Liquibase versichert Konsistenz über verschiedene Umgebungen (Prod, Dev, Staging etc.).
# Wichtige Konzepte

| Name               | Erklärung                                                                                                                                                 |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Changelogs**     | Dateien, die die Änderungen in einer Datenbank tracken.                                                                                                   |
| **Changesets**     | Sets an Änderungen, die an einer Datenbank angewendet werden. Sind Teil von Changelog-Dateien.                                                            |
| **Change-Types**   | Datenbankunabhängige Operationen, die in den Changesets definiert werden und zum Updaten der Datenbanken genutzt werden (zB. um eine Column hinzuzufügen) |
| **Changelog-Tags** | Helfen bei der Kontrolle davon, wann und zu welcher Datenbank Änderungen gemacht werden sollen.                                                           |
