#schule 
#m162

“*Das konzeptionelle Datenmodell ist das, worüber man mit dem Kunden redet. Das logische Datenmodell ist das, worüber man mit den Programmierkollegen redet.*” - T. Kaufmann

## Konzeptionelles Datenmodell

Das Konzeptionelle Datenmodell stellt eine Sicht auf die in der Datenbank zu verwaltenden Daten dar. Es wird aufgrund der Anforderungen des Kunden erstellt und dient zur überprüfung mit dem Endkunden, ob an alles gedacht wurde. Es enthält Entitätsmengen, Attribute und Beziehungen. Dafür enthält es keine Details, also keine Primär- und Fremdschlüssel, Datentypen oder Zwischentabellen.

## Lernziele

1. Sie verstehen die Schritte zum Erstellen eines konzeptionellen Datenmodells
    1. Anforderungen aufnehmen
        
        Die Anforderungen beschreiben, was für Informationen in der Datenbank gebraucht werden und wie diese Strukturiert sein müssen. Beispielsweise kann eine Anforderung sein, dass alle Mitarbeiter eine bestimmte Liste von Daten haben müssen (Adresse, Geburtsdatum).
        
    2. Datenobjekte identifizieren
        
        In diesem Schritt wird anhand der Anforderungen die Objekte identifiziert. Zum Beispiel, dass Mitarbeiter und Produkte Datenobjekte sind.
        
    3. Merkmale der Datenobjekte definieren
        
        In diesem Schritt werden die Attribute der Datenobjekte festgelegt. ZB. dass jedes Produkt das Attribut Preis und jeder Mitarbeiter das Attribut Adresse hat.
        
    4. Von den Datenobjekten zu den Tabellen
        
        Ein Datenobjekt besteht entweder aus einem Datensatz oder wird aus mehreren Datensätzen zusammengesetzt (Datensätze aus unterschiedlichen Tabellen). Die 
        Datenobjekte erhalten wir mit Datenbankabfragen. Falls ein Datenobjekt 
        aus mehreren Datensätzen besteht, erfolgt die Abfrage über mehrere 
        Tabellen mittels JOIN. Beispielsweise hat jedes Objekt “Mitarbeiter” ein Objekt “Ort”, der “Mitarbeiter” wird also nicht nur aus Attributen, sondern auch aus einem anderen Objekt zusammengestellt (besteht aus Attributen + einem anderen Objekt)
        
    5. Beziehungen zwischen den Tabellen festlegen
        
        Nachdem man die Objekte und die Attribute festgelegt und sich eine Vorstellung der verschiedenen Tabellen angeeignet hat, muss man nun die Beziehungen zwischen diesen Tabellen definieren. Das macht man in einem ERD-Diagramm (Entity-Relationship-Diagramm). In diesem Diagramm wird die Beziehung von Objekten zueinander nach dem IEM-Modell dargestellt.
        
        ![Untitled](Schulmodule/M162%20-%20Datenbanken/Fotos%20&%20PDFs/Untitled%201.png)
        
2. Anhand von Anforderungen können Sie diese Schritte praktisch durchführen
3. Sie können Entity-Relationship-Diagramme erstellen