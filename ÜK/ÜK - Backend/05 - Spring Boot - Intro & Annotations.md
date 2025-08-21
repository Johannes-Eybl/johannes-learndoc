#ÜK
#backend
# Lernziele

- Wissen, was Spring Boot ist
- Wissen, wofür Spring Boot eingesetzt wird
- Ein Spring Boot-Projekt erstellen können

# Übersicht Spring Boot

Spring Boot ist ein Java-Basiertes Framework für die Entwicklung von Webanwendungen.

Spring arbeitet nach dem Prinzip “Convention over Configuration”.

### Definition Framework

Eine Sammlung von Klassen, die uns Arbeit abnehmen.

### Coding Richtlinien

### PascalCase

Für Klassennamen, Interfacenamen, Filenamen

### camelCase

Für Variabeln, Methoden

## Projekt Erstellen

In BBC immer Grade mit Groovy verwenden. Die Group ist immer “ch.bbcag”

Packaging “Jar” und Java 17. Bei Dependencies muss man “Spring Web” verwenden.

- start.spring.io
- Mit Intellij-Ultimate (!): Direkt bei “new Project” kann man links den “Spring Initializr” wählen.

# Annotations

Spring verwendet Annotations “@”, um im Hintergrund Klassen zu generieren.

## @RestController

Diese Klasse enthält Rest-Endpunkte

## @RequestMapping(””)

Definiert die URI des Controllers. Zb. mit `@RequestMapping("/greetings/")`

## @GetMapping / @PostMapping / @PatchMapping / @DeleteMapping

Bestimmt die http-Methode. Wenn über einer Methode geschrieben, wird diese Methode aufgerufen, wenn der entsprechende Befehl aufgerufen wird.

Mit etwas wie `@GetMapping(path = "{id}")` kann man auch eine Variabel im Path verarbeiten. Diese Variabel muss dann mit `@PathVariable` abgefragt werden.

Der Path im Browser wäre dann “/greetings/id”

## Methoden-Parameter

Mit `@RequestParam` kann man in der URI mitgegebende Variabeln auswerten. 

Ebenfalls möglich ist, default-Werte zu definieren:

`public List<Item> findItems(@RequestParam(required=false) String name);`

Will man Daten aus dem Body ziehen, muss man `@RequestBody` verwenden:

`public Item insert(@RequestBody Item item)`