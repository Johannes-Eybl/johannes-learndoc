#ÜK
#multiuser

# Ziele

- DIe Umsetzung einer objekt-relationalen Abbildung eines Geschäftsobjektmodells und deren Spezifikation mittels UML können
- Möglichkeiten kennen, wie man Transaktionen in der Applikation implementiert
- Möglichkeilten kennen, Transaktionen in der Applikation und dem DBMS zu Dokumentieren
- Ein Sequenzdiagramm lesen und verstehen können
- Transaktionen im einem Seqenzdiagramm lesen und verstehen können
- Transaktionen in Spring umsetzten können
- Locking am Richtigen Ort einsetzen können

# Transaktionen in Spring Boot

Obwohl Spring Boot standartmässig immer Transaktionen verwendet, muss man diese immer explizit mit `@Transaktion` angeben. So kann man die Art der Transaktion auch genauer steuern, zB. das Isolationslevel und für welche Exceptions ein Rollback gemacht werden soll (und für welche nicht).

`@Transactional` steuert und startet eine Transaktion. Die Annotation wird vorallem im Service verwendet, denn dort befindet sich die Businesslogik. 

# Locking - Optimistic vs Pessimistic

Beim Locking geht es darum, die Datenbank zu sperren, während man auf diese zugreift. So werden Konflikte verhindert. Es gibt zwei Prinzipien, auf die die Datenbank gelockt werden kann, Optimistic- und Pessimistic Locking.

Ein möglicher Fehler, bei dem Locking helfen kann, ist das Lost Update. Beim Lost Update liest Nutzer A Daten bevor Nutzer B diese Daten verändert. Will Nutzer A die Daten nun verändern, geht er von einem nicht aktuellen Stand der Datenbank aus. So können beispielsweise mehr Tickets verkauft werden als es Plätze gibt.

![Ausgangslage](ÜK/ÜK%20-%20Multiuser/Multiuser%20-%20PDFs%20&%20Fotos/Untitled%207.png)

Ausgangslage

## Optimistic Locking

Optimistic Locking erlaubt, dass der Conflict passiert und macht im Fall der Fälle ein Rollback.

Beim optimistic Locking gibt man der Entität eine Versionsnummer oder einen Timestamp. Wenn zwischen lesen und schreiben eine neue Version (durch einen anderen Nutzer) entstanden ist, wird ein Fehler geworfen und ein Rollback gestartet.

![Untitled](ÜK/ÜK%20-%20Multiuser/Multiuser%20-%20PDFs%20&%20Fotos/Untitled%201%201.png)

## Pessimistic Locking

Beim Pessimistic Locking wird ein Konflikt verhindert, in dem die Tabelle oder möglicherweise auch nur eine bestimmte Zeile komplett gesperrt werden. Wenn User A (Alice) von der DB liest, sperrt Sie diese für User B (Bob). Erst wenn A’s Änderungen committed werden, kann B auch updaten. Bis A committed, sind B’s updates geblockt.

![Untitled](ÜK/ÜK%20-%20Multiuser/Multiuser%20-%20PDFs%20&%20Fotos/Untitled%202%201.png)

# Rollbacks in Spring Boot

Wenn ein Service, der die `@Transactional`-Annotation hat, auf eine Exception stösst, wird ein Rollback ausgeführt. Praktisch kann das beispeilsweise beim Zusammenführen (mergen) zweier Instanzen mit “throw new” passieren.

# Arten von Locks

Es gibt eine Reihe von Locks, die man im Repository anwenden kann.

![Untitled](ÜK/ÜK%20-%20Multiuser/Multiuser%20-%20PDFs%20&%20Fotos/Untitled%203%201.png)