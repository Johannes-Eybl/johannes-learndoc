#ÜK
#multiuser

# Ziele

- Das Schichtenmodell der Informationssicherheit kennen
- Den Unterschied zwischen Authorization und Authentication kennen
- Das CIA-Dreieck kennen

# CIA

- **C**onfidentiality
    - Daten dürfen nur von autorisierten Nutzern gelesen werden
- **I**ntegrität
    - Daten dürfen nicht verfälscht werden. Die Exaktheit und Vollständigkeit muss gewährleistet sein. Änderungen mussen nachvollziehbar sein.
- **A**vailability
    - Daten müssen zugänglich sein. Verzögerungen und Ausfälle sind zu vermeiden

# Schichtenmodell TODO : Besser erklären

Das Auftrennen eines Systems in mehrere Schichten stärkt seine Sicherheit. Das kann physisch in Form von Verschlossenen Serverräumen, aber auch digital in Form von beispielsweise segmentierten Netzwerken erreicht werden. 

# Authentication (Login)

Autentikation ist die Verifizierung der Echtheit einer Eigenschaft. Das bedeutet, dass geprüft wird, ob jemand wirklich der ist, für den er sich ausgibt. Umgesetzt wird das beispielsweise mit Passwörtern, Sicherheitsfragen oder Biometrie wie Fingerabdruck oder Gesichtserkennung.

# Autorizierung (Rechte)

Autorizierung prüft die Rechte eines Nutzers. Konkret wird beispielsweise bei einer Spring-Applikation geprüft, welche CRUD-Operation ein Nutzer machen darf.