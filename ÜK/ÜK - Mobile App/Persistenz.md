#ÜK
#mobileApp

# Ziele

- Wissen, was Persistenz bedeutet
- Eine Persistenz-API nutzen können
- Offlineszenarien kennen
- Eine low Budget Lösung für Offlineszenarien kennen

# Was ist Persistenz

Persistenz ist das Speichern von Daten, sei es online oder offline. Es gibt viele verschiedene Arten und Weisen, Persistenz umzusetzen. Beliebt sind SQL, Cloudbasiert oder in JSON direkt im Dateisystem.

# Netinfo

NetInfo ist ein Package, welches von der Community gemanaged wird. Mit diesem Package kann man abfragen, ob man mit dem Internet verbunden ist und was für einen Verbindungstyp man hat.

# Offline-Szenarien

Offline-Szenarien sind sehr komplexe Probleme. Man kann zwar Daten offline zwischenspeichern und danach im Hintergrund synchronisieren, doch das bringt viele Probleme mit sich, besonders wenn mehrere Nutzer an der selben Datenbank arbeiten können (Multiuser)

# AsyncStorage

Es gibt den *useAsyncStorage-*Hook. Dieser Hook erlaubt es einem, Werte zu laden, Werte zu speichern, zu löschen und Werte zusammen zu führen (merge). Dieser Wert kann aber nur ein String sein. Wenn man Objekte und Arrays speichern will, muss man diese Serialisieren. Mit `JSON.stringify(myObjectArrayStuff)` kann man das realisieren.