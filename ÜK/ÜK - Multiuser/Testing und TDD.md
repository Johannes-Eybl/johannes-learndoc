#ÜK
#multiuser

# Ziele

- Relevante Aspekte, welche bei der Testspezifikation iner Multi-User-Applikation zu berücksichtigen sind kennen.
- Wissen, wie man nicht-funktionale Anforderungen testen kann
- Sich an verschiedene Testarten erinnern können
- Prinzipien des Unit-Testing kennen.
- Wissen, was TDD ist

# Warum testing

An eine Webabpplikation werden bestimmte anforderungen gestellt. Wenn diese Anforderungen nicht geprüft werden, kann eine Applikation enstehen, die nicht den Anforderungen enstpricht.

Wenn bestimmte Test häufig wiederholt werden, muss man sie automatisieren.

# Arten von Tests

## Unit-Tests

Die meistgenutzte Art von Tests. Langfristig am effizientesten.

## Integrationstest

Wird weit weniger als Unittests verwendet. Kombiniert mehrere Units mit Abhängigkeiten.

## Manuelle Tests

Werden am wenigsten verwendet. Gelten als Abnahmetest für den Kunden.

# FIRST

Das Ziel von FIRST ist das automatisierte Testen von einzelnen Methoden ohne Abhängigkeiten

- **F**ast
    - Vor jedem Check-In ausführen
    - Entwickler sollten nicht zögern, sie auszuführen
- **I**solated
    - Dürfen sich gegenseitig nicht beeinflussen
- **R**epeatable
    - Resultat bleibt immer das Gleiche
    - Testdaten werden gesetzt und nach dem Test gelöscht
- **S**elf-Validating
    - Das Resultat ist eindeutig Richtig oder Falsch
    - Jeder Test kann fehlschlagen
- **T**horough & **T**imely
    - Werden konsequent eingesetzt
    - Werden zum richtigen Zeitpunkt erstellt

# Test Driven Development (TDD)

Bei TDD wird vor dem Programmieren eines Components (oder Moduls) eine Reihe von Tests geschrieben. 

## Vorteile von TDD

- Code wird im Vorraus konzipiert und besser geplant
- Tests können nicht vergessen gehen
- TDD bietet eine Art absicherung vor unvorhergesehenen Bugs, da die Tests versteckte Fehler aufdecken sollen

## Ablauf von TDD

![Untitled](ÜK/ÜK%20-%20Multiuser/Multiuser%20-%20PDFs%20&%20Fotos/Untitled%205.png)

1. Neuen Unittest erstellen
    1. Commiten
    2. Abchecken dass der Test läuft und fehlschlägt
2. Code schreiben, der den Test zum laufen bringt
    1. Wirklich alle Tests nochmal laufen lassen
3. Code Cleanup
    1. Commiten