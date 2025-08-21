#ÜK
#multiuser

# Lernziele

- Kennt die wichtigen Architekturvarianten und -konzepte
    - Client / Server
    - Multitier
    - Middleware
    - Framework
    - Klassenbibliothek
- Wissen, was man unter Softwarearchitektur versteht
- Vor- und Nachteile verschiedener Architekturen kennen
- Wissen, worauf man beim Entwurf der Softwarearchitektur bei Multiuser-Applikationen achten muss

# Begriffe

## Modul

Ein Modul ist eine funktionale Einheit wie eine Datenverwaltung, Zeiterfassung oder das Gradebook vom BBC. Die Extranet-Webseite ist beispielsweise in kleinere Module unterteilt.

## System / Applikation

So wie die Extranet-Webseite ist eine Applikation / ein System eine ansammlung von kombinierten Modulen, welche zusammen einen Zweck erfüllen.

## Systemgrenzen

Systemgrenzen sind Schnittstellen zu anderen Systemen wie Google / Faceboook oder auch ein selber geschriebenes Modul

## Schichten

### Physikalische Schichten

…sind mehrere Computer, die an unterschiedlichen Standorten stehen können

### Logische Schichten

…sind Aufteilungen innerhalb einer Software. Der Zugriff / Austausch zwischen den Schichten ist genau beschrieben. Logische Schichten sind in der Fallstudie Präsentations-, Business- und Persistenzschicht. 

## Zusammenfassung Begriffe

Module sind vertikal aufgebaut, Schichten horizontal.

Ein Modul ist in Persistenz-, Business- und Präsentationsschicht aufgeteilt.

Ein System besteht aus mehreren Modulen.

# Was ist Softwarearchitektur

Softwarearchitektur beschreibt, auf welche Weise ein System / eine Software zusammengesetzt ist.

Software wird in kleinere Komponenten aufgeteilt, die untereinander mit klar definierten Schnittstellen (APIs) arbeiten. Die Architektur ist entscheident für die Erfüllung der Systemanforderungen.

# Wozu braucht es Softwarearchitektur

## Übersicht

Eine klar definierte Architektur macht es einfacher, sich im System zurechtzufinden. 

## Wiederverwendbar

Da Module und Schichten voneinander getrennt sind, kann man diese austauschen. Fachbegriff hier ist “Entkoppelung”.

## Skalierbar

Voneinander gelöste Schichten und Module können redundant bereitgestellt werden. 

## Wartbar

Fehler in der Applikation sind dank entkoppelten Schichten und Modulen leichter zu beheben.

## Parallelisierbare Entwicklung

Für die Entwicklung können die Schnittstellen der verschiedenen Module definiert werden und einzeln entwickelt werden.

# Architekturarten

Je nach Architektur werden unterschiedlich viele Schichten verwendet. Man beschreibt die Menge der Schichten (Physich und Logisch) mit Tiers.

## 1-Tier Architektur

Darstellungsschicht, Businesslogik und Datenhaltung (Persistenzschicht) befinden sich auf dem selben Gerär

## 2-Tier Architektur

Hier wird beispielsweise die Datenbank auf ein zweites Gerät ausgelagert. Die Persistenzschicht ist somit auf das zweite Gerät verlagert worden.

## 3-Tier Architektur

Die häufigste Architektur. Die meisten Webseiten und auch Videospiele verwenden diese Art von Architektur. 

Hier werden Präsentations-, Applikations- und Persistenzschicht auf 3 Geräte aufgeteilt. 

## n-Tier Architektur

Hier werden die drei Schichten auf eine beliebige Anzahl von Servern verteilt. So kann man redundante Schichten haben, was für Load-Balancing gebraucht wird. Ausserdem kann man verschiedene Services auf verschiedenen Servern haben,

Die n-Tier Architektur wird beispielsweise im Gaming-Bereich angewandt.