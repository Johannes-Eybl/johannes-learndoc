#ÜK
#backend
# Ziele

- Verstehen, was REST &  RESTful bedeuten
- Wissen, was CRUD ist
- Den OpenAPI-Standart kennen

# Rest / RESTful

REpresentational State Transfer ist ein Architekturstil zum Datenaustausch

- Client-Server Modell (der passive Server wartet auf Anfragen vom aktiven Client)
- Einheitliche Schnittstelle (jede Ressource hat eine bestimmte URI, mit der sie addressiert werden kann.
- Zustandlos (Stateless) (Jede Anfrage an den Sever muss alle Informationen beinhalten, welche zum Interpretieren der Anfrage notwendig sind.)
- Cachable (Das Backend kann verschiedene Resultate cachen, also zwischenspeichern um schnellere Datenverarbeitung und weniger Datenbank-Queries zu haben)

# REST Ressource

Der Endpunkt einer API ist die URI. Bei der werden keine Verben, sondern Nomen verwendet. 

Diese Werte lassen sich auch geschachtelt darstellen, zB. `/items/1/tag/` 

Man kann diese HTTP-Requests auch mit POST; GET; PATCH und DELETE machen.

## CRUD und HTTP

- Create → POST
- Read → GET
- Update → Patch
- Delete → Deleteyya