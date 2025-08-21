#ÜK
#backend

# Lernziele

- Abfolge zwischen Request und Response kennen
- Wissen, was ein Webserver ist und welche Dienste er leistet
- Wissen, wo server- und wo clientseitige Skripsprachen eingesetzt werden
- Die wichtigsten Fachbegriffe des HTTP-Protokolls kennen

# Was Webserver?

Ein Webserver liefert Dokumente an Clients. Diese Dokumente können fertige HTML-Seiten sein, aber auch Bilder, JS oder CSS sind möglich.

Weitere Funktionen eines Webservers sind Zugriffsbeschränkungen, Sicherheitsgarantieen (mit HTTPS), Logs und Cashing.

Die Kommunikation mit dem Client basiert auf Anfrage und Antwort. Die Anfragen geschehen mit einer Request-URL. Diese URL hat eine so genannte URI (uniform ressource identifier), in der Variabeln mitgegeben werden können. Das ist zwar nicht sicher (da einfach einsehbar), doch man kann die URI kopieren und auf einem anderen Gerät eingeben und erhält jedes Mal dasselbe Ergebnis.

![Untitled](ÜK/ÜK%20-%20Backend/Fotos%20&%20PDF's/Untitled.png)

# Header & Body

Der Header ist wie die Etikette auf einem Postpaket. Er enthält Metadaten wie:

- Dateiformat
- Zeichenkodierung
- User-Agent
- Authorisation
- Location

Der Body ist wie der Inhalt des Pakets. Er enthält alle Daten, also JSON, HTML oder ähnliches.

# Request-Arten

## GET

Übertragung in der URL mit den Zeichen *? = &*

## POST, PUT und PATCH

Wird im Packetbody übertragen. Ist also nicht in der URL sichbar, *aber deshalb nicht sicherer*

## DELETE

Wird in der URL übertragen

# Response Codes

- 100 → Informationen
- 200 → Success!
- 300 → Um- /Weiterleitung
- 400 → Client Error (z.B. 400 bad request)
- 500 → Server Error (zB. 500 internal sever error)