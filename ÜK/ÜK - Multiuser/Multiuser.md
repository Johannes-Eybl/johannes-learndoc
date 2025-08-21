#ÜK
#multiuser

# Ziele

- Anforderungen an das Datenbankmanagement-System bezüglich Multi-User-Fähigkeit kennen
- Möglichkeiten kennen, ein mehrbenutzerfähiges Rechtemanagement zuer implementieren
- Die wichtigsten Aspekte einer multiuserfähigen Applikation kennen
- Die Herausforderungen im Zusammenhang mit Multiuserfähigkeit kennen
- Benutzer in der Datenbank anlegen und berechtigen können

# Was bedeutet Multiuserfähigkeit

In einer multiuserfähigen Applikation können mehrere Benutzer gleichzeitig auf ein System zugreifen. Jeder Benutzer hat einen eigenen Prozess, der je nach Architektur auf unterschiedlichen Rechnern läuft. 

# Herausforderungen

## Security

Siehe Secruity-Präsi bzw. Zusammenfassung

## Performance

Da die Infrastruktur bei mehreren Usern stärker belastet wird, enstehen folgende Prrobleme:

- Lange Antwortzeiten
- Hoher Ressourcenverbrauch
- Geringe Stabilität

## Portabilität

Hier sind  verschiedene  Medien wie Desktop, Mobile usw. gemeint

## Wartbarkeit

- Clean COde
- Tests
- Dokumentation

## Nebenläufigkeit

Wenn mehrere Nutzer gleichzeitig mit einer Datenbank interagieren wollen, können probleme entstehen. Es können:

- Daten überschrieben werden → *Lost Update*
- Warteabhängigkeiten enstehen → *Deadlock*