#notComplete
#programming

UML → Unified Modeling Language

Statisch → Struktur eines Systems

Dynamisch → Verhalten eines Systems

# Object Diagram - Aufbau

Klasse → Fasst alle Objekte mit ihren Gemeinsamkeiten zusammen

Objekt → Eine individuelle Ausprägung einer Klasse


### Kennzeichnung von Zugang

In dem man vor die Variabeln und Methoden folgende Zeichen setzt, kann man diese als private / public / etc festlegen

public → +

private → -

protected → #

package → ~

# Klassendiagram Diagram - Assoziazion

Assoziation → Verknüpfung / Beziehung von Klassen zu einander

## Multiplizitäten (Wie viele Objekte einer Klasse mit wie vielen Objekten einer anderen Klasse in Beziehung stehen)

### Einfache Multiplizitäten

Jedes Auto hat einen Eigentümer, jeder Eigentümer hat keine oder beliebig viele Autos


# Aggregation

*Die Klassen können trotz ihrer Bindung auch unabhängig von einander existieren!*


Ein Beispiel dafür wäre Auto (Klasse1) und Fahrer (Klasse2)

# Komposition

Klasse 1 (Aggregationsklasse) erstellt Klasse 2 (Teilklasse). Das bedeutet, dass die Teilklasse mit der Aggregationsklasse lebt und stirbt.

Beispiel → Der Computer erweckt und tötet das Betriebssystem wenn er geboren wird oder stirbt.


Ein Beispiel ist Auto (Klasse1) und Kofferraum (Klasse2). Ohne Auto kein Kofferraum


Mit einem Pfeil kann man festlegen, welche Klasse von welcher anderen abhängig ist

# Vererbung

Klasse 2 erbt von Klasse 1

# In IntelliJ ein Diagramm bauen

Alle Klassen auswählen → Rechtsklick → “Show Diagram”