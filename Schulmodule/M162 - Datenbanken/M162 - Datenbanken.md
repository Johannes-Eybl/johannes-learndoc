#schule 
#m162

# Lernziele 1

- Ich weiss, was analoge und digitale Signale und Daten sind
    - Analoge Daten sind stufenlos und tragen damit theoretisch unendlich viele Informationen.
    - Analoge Daten sind zb. alles was man hört und alles, was man sieht (Licht- und Schallwellen)
    - Digitale Daten sind alle Informationen, die elektronisch gesammelt und weiterverarbeitet werden können.
- Ich weiss, was Daten sind und wie Datentypen unterschieden werden können
    - Daten sind messbare Informationen, wie zb. Zahlenwerte oder formulierbare Befunde
- Ich kenne den Unterschied zwischen unstrukturierten, semistrukturierten und strukturierten Daten.
    - Unstrukturierte Daten können nicht einfach in einer Tabelle organisiert werden, sondern brauchen meistens eigene Software für deren Organisation. Gute Beispiele sind Fotos oder Audio-Dateien. Meistens sind unstrukturierte Daten ganze Dateien.
    - Semistrukturierte Daten sind Informationen, die keine allgemeine Struktur haben, sondern einen Teil der Strukturinformation mit sich tragen. Ein gutes Beispiel dafür ist ein Word-Dokument, das mit Titeln und Inhaltsverzeichnis zwar eine Struktur hat, aber nicht mit anderen Dokumenten vergleichen lässt.
    - Strukturierte Daten können in Datenbanksystemen gespeichert werden und haben ein vorgegebenes Format wie Kunden oder Produkte.
- Ich weis, was Redundanzen und Inkonsistenzen sind.
    - Redundanzen sind Informationen, die mehrfach vorkommen, aber mit einer Umstrukturierung nur einmal vorkommen müssten (kein Informationsverlust durch das weglassen von Kopien)
    - Inkonsistenzen sind Wiedersprüchlichkeiten zwischen Daten. Zum Beispiel wenn der Name einer Stadt mehrmals unterschieldich geschrieben vorkommt.
- Ich kann in einer Exceldatei Suchen und Auswertungen durchführen
- Ich kenne die Vor- und Nachteile der Verwaltung von Daten in Excel
    - Vorteil: Nutzerfreundliche Verwaltung und Strukturierung von Daten
    - Vorteil: Einfaches grafisches Bearbeiten von Tabellen
    - Nachteil: Wird bei grossen Datenmengen unübersichtlich
    - Nachteil: Das verlinken von Tabellen mit Primär- und Sekondärschlüsseln ist aufwendig, da das Programm nicht dafür gemacht ist.

# Lernziele 2

- Ich kenne Ubuntu und kann damit arbeiten
    - Ubuntu ist einer der bekanntesten Linux-Distributionen
- Ich kenne SQLite und kann damit arbeiten
- Ich habe erste Erfahrungen mit einer relatonalen Datenbank gemacht.
- Ich weiss, was Tabellen in einer relationalen Datenbank sind.
    - In einer relationalen Datenbank werden Tabellen auch Relationen genannt. Einer Relation ist entweder eine Tabelle, Teile einer Tabelle oder der Verbund von mehreren Tabellen.
    - Definition Tabelle:
        - Jede Tabelle hat einen eindeutigen Namen
        - Eine Tabelle besteht aus Attributen (Spalten) und Datensätzen/Entitäten (Zeilen)
        - Jedes Attribut hat einen einzigartigen, eindeutigen Namen
        - Ein Attribut, das ein Primärschlüssel ist, identifiziert einen Datensatz in einer Tabelle mit der ID
        - Die Einträge in einer Tabelle bezeichnet man als Datensätze
- Ich weiss, was Beziehungen zwischen Tabellen in einer relationalen Datenbank sind.
    - Beziehungen zwischen Tabellen werden mit hilfe von Primär- und Fremdschlüsseln aufgebaut. Jeder Fremdschlüsselwert muss als Primärschlüssel in  der Primärtabelle existieren.
- Ich kenne das Konzept mit Primär- und Fremdschlüsseln
    - Ein Primärschlüssel wird zur eindeutigen Identifizierung eines Datensatzes innerhalb einer tabelle verwendet.
    - Ein Fremdschlüssel ist ein Attribut einer Tabelle, welches auf den Primärschlüssel einer anderen Tabelle verweist.
- Ich kenne die möglichen Beziehungstypen und kann die Beziehung zwischen zwei Mengen bestimmen.
    1. Einfache Beziehung:
        - 1: Jede Entität (Zeile) der ersten Entitätsmenge steht mit genau einer Entität der zweiten Entitätsmenge in Beziehung
    2. Konditionellle Beziehung
        - c: Jede Entität der ersten Entitätsmenge steht mit höchstens einer Entität der zweiten Entitätsmenge in Beziehung.
    3. Mehrfache Beziehung:
        - m: Jede Entität der ersten Entitätsmenge steht mit mindestens einer Entität der zweiten Entitätsmenge in Beziehung
    4. Mehrfachkonditionelle Beziehung:
        - mc: Jede Entität der ersten Entitätsmenge kann mit beliebig vielen Entitäten der zweiten Entitätsmenge in Beziehung stehen.
    

# Lernziele 3

- Sie wissen, was eine relationale Datenbank ist
    - Eine Relation kann zwischen Attributen und Entitäten bestehen, aber auch zwischen zwei Tabellen existieren.
- Entitätstyp / Tabellendefinition: Der Name einer Tabelle, welche eine Menge von Attributen (Eigenschaften) enthält. Bsp: Entitätstyp Mitarbeiter enthält Attribute Name, Lohn, Adresse.
- Sie kennen die Begriffe von Relationalen Datenbanksystemen und deren Bedeutung
    - Entität / Tupel / Datensatz: Eine Zeile einer Tabelle, ein einzelner Eintrag.
    - Entitätsmenge / Tabelle: Die Menge aller Datenobjekte mit demselben Entitätstyp, sprich alle Datensätze einer Tabelle.
    - Attribut / Merkmal: Die Spalten einer Tabelle, also die Eigenschaften der Entitäten. Hat einen bestimmten Namen und Datentypen.
    - Datentypen: Sind identisch mit denen von Programmiersprachen → String, Int etc.
    - Wertebereich / Domäne: Der zugelassene Bereich, in dem ein Wert sein kann. Zb muss eine Telefonnummer 10 stellen haben.
    - Attributwert: Der genaue Wert eines Attributes eiener bestimmten Entität.
- Sie kennen die Begriffe des Entity-Relationship-Modells und deren Bedeutung.
- Sie wissen, was Redundanzen sind und wie diese vermieden werden können.
    - Redundanzen sind doppelte Informationen in einer Datenbank. Man spricht nur bei Daten aus der realen Welt von redundanzen, also zählen Schlüssel nicht dazu.
    - Man vermeidet Redundanzen mit neuen Tabellen, die diese Daten zusammenfassen und mit Primärschlüsseln identifizieren. Dann muss in anderen Tabellen nur noch der Primärschlüssel angegeben werden.
- Sie wissen, was eine konsistente Datenbank ist und wie dies erreicht werden kann.
    - Konsistenz ist die Freiheit von Wiedersprüchen (bzw Redundanzen) innerhalb einer Datenbank.
    - Konstistenz bedeutet die Überinstimmung von an verschiedenen Stellen gespeicherter Daten oder des Bezugs zwischen Daten in der Datenablage. Als inkonsistent werden wiedersprechende Daten bezeichnet.
    

# Lernziele 4

- Sie können Redundanzen erkennen
- Sie können Inkonstistenzen und Anomalien vermeiden
    - Konsistenz wird durch drei folgene Massnahmen erreicht:
        1. Keine Redundanzen
        2. Das ACID-Prinzip
            - Atomicity: Bei einer Transaktion muss jede Veränderung der DB klappen - oder keiner.
            - Konstistenz: Die DB wird nur auf vorhersebare (konsistente) Weise verändert.
            - Isolation: Es werden nicht mehrere Transaktionen (Veränderungen) der DB auf einmal gemacht, sondern nach einander.
            - Dauerhaftigkeit: Jede Transaktion muss dauerhaft gespeichert sein.
    - Anomalien treten bei nicht existierenden oder fehlerhaften Normalisierungen auf. Es gibt mehrere Arten von Anomalien:
        - Update-Anomalie: Wenn gleiche Daten unterschiedlich benennt wurden und darum bei einem Update / einer Transaktion nur teile der Datenbank verändert werden.
        - Delete-Anomalie: Wenn durch das Löschen einer Entität ungewollt Informationen verloren gehen.
        - Insert-Anomalie: Wenn Attribute Fehlen, mehrere Primärschlüssel die selbe Information tragen oder ein Objekt mehrere Schlüssel trägt.
- Sie verstehen die formelle Normalisierung → Von der nullten bis zur dritten Normalform
    - Normalisierung ist die Überführung einer Datenbanktabelle in eine Normalform höheren Grades. Es ist die Aufteilung von Attributen in mehrer Tabellen mit dem Ziel, Redundanzen zu verringern (bzw komplett zu verhindern)
    - Nullte Normalform: Eine Tabelle ist in der nullten Normalform, wenn alle Daten der realen Welt darin unstrukturiert aufgefasst sind. In so einer Tabelle können in einem Attributwert auch mehrere Informationen gelistet sein (was in einer DB nicht vorkommen sollte (atomarität)).
    - Erste Normalform: Wenn alle Daten atomar vorliegen (pro Attributwert nur ein Wert), ist die Tabelle in der ersten Normalform. Man trennt also alle Informationen in die kleinst mögliche Einheit auf (die Sinn ergibt) und gibt ihr eine eigene Spalte (macht sie zu einem eigenen Attribut)
    - Zweite Normalform: Wenn die Attribute einer Tabelle nur von Primärschlüsseln abhängig sind, ist sie automatisch bereits in der zweiten Normalform. Der Unterschied zur ersten Normalform besteht darin, dass jedes Attribut von den Schlüsseln abhängig ist. Es können jedoch immernoch Abängigkeiten von Attributen untereinander bestehen wie zb. die Abhängigkeit von Name zu Kundennummer.
    - Dritte Normalform: In Tabellen der dritten Normalform sind alle Attribute der Tabelle nur noch von ihrem Primärschlüssel und nicht mehr von anderen Attributen abhängig.                    Es werden sperate Tabellen gemacht, die nur dafür da sind, die Schlüssel verschiedener Tabellen (Einkäufe, Kunden) zu verbinden.
- Sie können die Normalisierung praktisch durchführen

### Abhängigkeiten

- Funktionale Abhängigkeit
    - Eine Funktionale Abhängigkeit besteht, wenn ein Attribut nur von einem Teil zweier Schlüssel abhängig ist.
- Vollständig funktionale Abhängigkeit
    - Vollständig funktional Abhängig ist ein Attribut, wenn es von allen Schlüsseln der Tabelle abhängig ist.
- Transitive Abhängigkeit
    - Transitiv Abhängig ist ein Attribut, wenn es von einem Nichtschlüsselattribut abhängig ist.

