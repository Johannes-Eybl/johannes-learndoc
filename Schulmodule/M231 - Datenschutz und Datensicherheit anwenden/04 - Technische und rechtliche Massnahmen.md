#schule 
#m231
# Ziele

- Einige technische Massnahmen kennen und deren Beitrag zur Informationssicherheit erklären
- Die grundlegende Aspekte eines Backup-Konzepts erklären
- Ein einfaches Zonenkonzept interpretieren
- Aufzeigen, wordurch Systeme gehärtet werden
- Die znetralen Faktoren zur Sicherung von WLANs aufzeigen
- Erklären, was unter ‘rechtlichen Massnahmen’ verstanden wird

# Backup

Ein Backup ist eine Kopie von wichtigen Daten. Auf diese kann im Notfall zurückgegriffen werden.

- Das Backup schützt vor den kosten, die durch einen Datenverlust entstehen
- Das Backup ist auch ein Datenarchiv. Unternehmen können damit die Sorgfalts- und Archivierungspflicht einhalten, welche vom Bund vorgegeben wird.

## Backup-Strategien

### Volle Datensicherung

Alle Daten werden gesichert

### Differenzielle Datensicherung

Alle Daten seit der letzten Vollsicherung werden gesichert

### Inkrementelle Datensicherung

Alle Daten seite der letzten Vollsicherung oder seite der letzen inkrementellen Sicherung werden gesichert.

### Virtuelle Volldatensicherung

Eine Software erstellt aus Vollsicherung und inkrementellen Sicherungen wieder eine vollständige Sicherung

### Imagebasierte Datensicherung

Der gesamte Datenträger (oder Container) wird gesichert. Sinnvoll für schelles Recovery in ganz schlimmen Fällen.

## Das Generationenprinzip

Das Generationenprinzip ist eine Strategie zur Datensicherung, bei der immer mehrere Sicherungen in verschiedenen zeitlichen Abstufungen vorhanden sind. 

Es gibt Tägliche (’Sohn’), wöchentliche (’Vater’) und monatliche (’Grossvater’) Backups. Durch diese Aufteilung wird ein zuverlässige und wiederherstellbare Sicherung der Daten gewährleistet.

## Disaster Recovery

Bei einem totalen Systemausfall kann es sehr lange dauern, alle Server und Controller wieder zum laufen zu bekommen. Mit Disaster-Recovery-Lösungen kann man Systeme möglichst schnell wieder herstellen. Dazu werden direkt virtuelle Maschienen gesichert bzw. auf ein anderes System gespiegelt

# Netztrennung durch Firewalls

Ein Plan für den Aufbau des Netzwerks wird *Zonenkonzept* genannt.

## Typische Firewall-Einsatzszenarien

### Bastion Host

Trennt LAN von WAN mit einer Firewall

### Three-Homed Firewall

Der Schutz mehrerer privater Netze mit nur einer Firewall

### Screened Subnet

Das Auftrennen verschiedener privater Netze, mit Firewall getrennt. Die Netze sind an einander gehängt, das mit den geringsten Sicherheitsanforderungen ist zwischen LAN und WAN.

## Firewall-Typen

### Statische Paketfilter-Firewall

Sequenzielles Regelsystem - Access Control List zb. mit IP oder Port

### Dynamische Paketfilter-Firewall

Hier wird der Paketfilter um die Funktion des Kontextbetrachtung der Verbindung erweitert. 

### Application Threat Management

Integration von Zusatzsicherheit auf den Sicherheitsgateways

### Personal Firewall

Softwarebasierte Firewall auf einem Clientsystem

# Sicherung von WLANs

## SSID

Die SSID darf keine Rückschlussmöglichkeiten bieten.

## WPA2&WPA3

Die Verschlüsselung des WLANs sollte mit WPA2 oder höher umgesetzt werden.

## WPS

WPS hat bekannte Schwachstellen, weshalb es deaktiviert werden sollte.

## Firmware

Immer die Firmware des Routers aktuell halten.

# ‘Härten’ von Systemen

## Richtlinien definieren

Zb. mit Gruppenrechten und Firewall-Einstellungen

## Hardware sichern

Gehäuse abschliessen, Festplatten verschlüsseln, nicht benötigte Schnittstellen deaktivieren, Notebooks verschliessen usw.

## Hardware aktuell halten

BIOS aktualisieren

## Betriebssystem sichern

Sicheres Betriebssystem verwenden, standartkonten deaktivieren, Rechte von Nutzern einschränken, nicht benötigte Dienste und Software deinstallieren.

# Mehrfaktor-Authentisierung

Es gibt viele Arten der mehrfaktor-Authentisierung. Hier sind ein paar Kategorien, in die die verschiedenen Versionen aufgeteilt sind:

## What you know

Passwort, PIN

## What you have

Smartcard, Token

## What your are

Fingerabdruck, Handschrift, Iris, Stimme (Biometrie)

# Rechtliche Massnahmen

Unter diesen Begriff fallen alle Massnahmen zur Einhaltung der gesetzlichen Vorgaben. Dazu gehören Archivierungspflichten und die Umsetzung des Datenschutzgesetzes.