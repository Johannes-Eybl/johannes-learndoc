#ÜK
#datenbanken

# Schlüssel
## Arten von Schlüsseln

### Primärschlüssel

Jeder Entitätstyp muss einen Primärschlüssel besitzen, welcher eindeutig ist und keine Nullwerte enthält. Dieser Primärschlüssel kann sich auch aus mehreren Attributen zusammensetzen, darf aber keine Überflüssigen Attribute enthalten (streicht man ein Attribut, *darf* der Schlüssel nicht mehr eindeutig sein). Auch bei der Eingabe von neuen Datensätzen dürfen die Schlüssel ihe Eindeutigkeit nicht verlieren.

! PK wird ein # vorne angesetzt

! Künstliche PK heissen immer “id”

### Fremdschlüssel

Attribut eines Entitätstypen, welches in einer anderen Entitätsmenge Primärschlüssel ist (”Verweis, Zeiger”)

! Falls der Fremdschlüssel auf einen natürlichen Primärschlüssel verweist, wird der Name nach dem Schema *herkunftstabelle_attribut* definiert

! Falls der Fremdschlüssel auf einen künstlichen Primärschlüssel verweist, wird der Name nach dem Schema *herkunftstabelle_id* definiert

### Natürliche Primärschlüssel

Kann ein Schlüssel aus den bestehenden Atrributen gebildet werden, ist dies ein natürlicher Schlüssel

### Künstliche Primärschlüssel

Kann kein Schlüssel aus bestehenden Attributen gebildet werden, wird ein künstlicher Schlüssel generiert. Das ist normalerweise eine ID-Nummer

# Normalisierung Vorgehen (Abhängigkeiten)

## Ziele

- Du verstehst, was mit folgenden Abhängigkeiten gemeint ist:
    - Funktionale Abhängigkeit
    - Volle Abhängigkeit
    - Transitive Abhängigkeit
- Du kannst Daten bis zu dritten Normalform normalisieren

## Abhängigkeiten

### Funktionale Abhängigkeit

Wenn Wert B von Wert A abhängig ist, zB das Gewicht des Autos vom Typ

### Volle Abhängigkeit

Wenn C von A und B abhängig ist, zB eine grüne (A) Aprikose (B) ist sauer (C) und eine orange (A) Aprikose (B) ist süss (C)


### Transitive Abhängikeit

Bei einer Transitiven Abhängigkeit ist A von B und B von C abhängig, aber nicht A von C.



## Normalisierung

### Erste Normalform

Um die erste Normalform zu erreichen. erstellen wir neue Entitäten (Zeilen), so dass pro Attribut nur noch ein einzelner Wert vorhanden ist (atomar). Ist das der Fall, hat man die erste Normalform erreicht.

### Zweite Normalform

Um die zweite Normalform zu erreichen, müssen alle *vollen Abhängigkeiten* aufgelöst werden. Dafür muss die Tabelle aufgeteilt werden. Damit man die Daten aber wieder zusammenführen kann, müssen diese eine Referenz haben, zB. eine ID.

### Dritte Normalform

Um die dritte Normalform zu erreichen, müssen alle transitiven Abhängigkeiten aufgelöst werden.

# Normalisieren Warum (Anomalien)

## Ziele

- Du verstehst, warum man normalisieren muss
- Du erkennst Abhängigkeiten von Daten
- Du kannst die ersten drei Normalisierungsschritte durchführen

## Warum normalisieren?

Normalisiert wird, damit Redundanzen beiseitigt und Anomalien vermieden werden.

## Anomalien

### INSERT-Anomalie

Wenn beim Eintragen einer Information auch eine andere, nicht zugehörige, Information erfasst werden muss.  



In dieser Tabelle muss beim Eintragen eines PCs auch ein Mitarbeiter erfasst werden und umgekehrt.

### UPDATE-Anomalie

Wenn eine Information an mehreren Orten vorhanden ist und darum überall auf einmal geupdated werden muss. Das kann dazu führen, dass die Information an zwei Orten unterschiedlich ist (inkonsistenz).

### DELETE-Anomalie

Beim Löschen eines Tabelleneintrags gehen auch Informationen verloren, die nicht zum Eintrag gehören.