#ÜK
#backend

# Parameter - Annotations:

## `@RequestParam`

Wird für Values in der URI benutzt. 

`myFunction(@RequestParam(value = "xyz", defaultValue = "lorem") String xyz)`

Wird verwendet bei: localhost/?xyz=”wdad”

## `@RequestBody`

Wird für Values im HTTP-Body verwendet. 

`myFunction(@RequestBody String xyz)`

## `@PathVariable`

Wird für Werte innerhalb des Pfades verwendet, die sich verändern können, wie zum Beispiel /id/.

# Datenbank / Entitäten - Annotations

Klassen, die eine Entität repräsentieren, müssen als `@Entity` gekennzeichnet werden.

Die verschiedenen Attribute dieser Entitäten werden als Variabeln gespeichert. 

Der Primärschlüssel wird mit `@Id` gekennzeichnet.

## Zusä