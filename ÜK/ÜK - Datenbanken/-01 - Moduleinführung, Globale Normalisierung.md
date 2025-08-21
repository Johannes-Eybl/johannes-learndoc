#ÜK
#datenbanken
## Daten sind überall & Daten sind teuer

Es werden überall ständig Daten über uns, andere und unser Umfeld gespeichert. Diese Daten sind vorallem für Firmen sehr wichtig, welche die Daten in Datenbanken organisieren. Firmen zahlen mittlerweile riesige Beträge, um Daten zu erwerben. Es sind wichtige Ressourcen der heutigen Welt.

## Client-Server-Datenbanken

- Zeile = Datensatz
- Spalte = Attribut

# Globale Normalisierung

## Ziele

- Entwurfmethode verstehen und anwenden können
- Beziehungen definieren können
- Begriffe kennen und erklären können
- Enitiy-Relationship-Diagram (ERD) lesen, verstehen und anwenden können

Lernziele offiziell:

[https://www.modulbaukasten.ch/module/106/1/de-DE?title=Datenbanken-abfragen,-bearbeiten-und-warten](https://www.modulbaukasten.ch/module/106/1/de-DE?title=Datenbanken-abfragen,-bearbeiten-und-warten)

**Man darf keine eigenen Notizen haben, aber alle vom BBC gegebenen Unterlagen (Aufgaben, PowerPoints etc.) für die Prüfung verwenden!**

## 6 Schritte zum Datenbank-Entwurf

1. Abstecken des Problemrahmens
    - Problem definieren
    - Problem analysieren und abgrenzen
    - Substantive (Namenswörter) suchen und hervorheben
2. Bildung von Entitätstypen und Attributen
    - Entitätstypen definiere
    - Mögliche Attribute zuordnen
    - Entitätstypen zeichnen
3. Festlegen von Beziehungen
    - Entitätstypen verbinden
    - Art der Kardinalität (Beziehung) festlegen
        - m → 1 oder mehrere (must)
        - c → 0 oder 1 (can)
        - mc → 0, 1 oder mehrere (must-can)
4. Beziehungen überprüfen
    
    Beim Überprüfen der Beziehungen muss man schauen, welche Beziehungen man so direkt in die Datenbank übertragen kann und welche Beziehungen mit Hilfe von Zwischentabellen auflösen muss.
    
5. Tabellenstruktur erstellen
6. Definition von Identifikationsschlüsseln

## BBC-Namenskonventionen

- Fremschlüssel werden nach dem Schema “Attributname_id” benannt

# Entity-Relationship-Diagram

## Ziele

- Du erstellst mit MySQL Workbensch ERDs in der Martin-Notation (Krähenfuss)

## Martin-Notation

- Gelbe Glühbirne = Primärschlüsel
- Roter Diamant = Fremdschlüssel
- Rote Glühbirne = Fremd- und Primärschlüssel zugleich
- Ausgefüllter Diamant = Muss ausgefüllt sein
- Nicht ausgefüllter Diamant = Kann leer sein

Wenn eine Tabelle keinen Primärschlüssel hat, sondern ein Fremdschlüssel auch ein Primärschlüssel ist, sind die Linien zu dieser Tabelle hin nicht ausgefüllt sondern gestrichelt.
