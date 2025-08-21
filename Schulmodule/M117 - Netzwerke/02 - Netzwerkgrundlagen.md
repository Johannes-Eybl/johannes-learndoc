#schule 
#m117
# Lernziele

- Netzwerktopologien und deren Vor- und Nachteile, sowie Einsatzzwecke erläutern.
- Die Bezeichnungen für die unterschiedlichen Netzwerkausdehnungen an Beispielen erläutern
- Netzwerk Schichtenmodelle und deren Aufbau, sowie deren Verwendungszweck erklären

# Netztopologie

Die Topologie ist die Struktur der Verbindung mehrerer Geräte, die im Netzwerk sind. Dabei unterscheidet man zwischen der physischen Topologie (Aufbau der Netzwerkverkabelung) und der logischen Topologie, welche den Datenfluss zwischen Endgeräten beschreibt.

Es gibt verschiedene Arten von Topologien;

- Punkt zu Punkt
    
    Bei einer Punkt zu Punkt-Topologie ist jeder Teilnehmer des Netzwerks direkt mit jedem anderen Teilnehmer verbunden. Das ist theoretisch zwar möglich, praktisch aber zu aufwendig & teuer.
    
- Ring
    
    Bei einer Ringtopologie ist jeder Netzwerkteilnehmer nur mit seinem direkten Nachbarn verbunden. Das Problem mit dieser Netzwerktopologie ist, dass ein Unterbruch des Rings das gesamte Netzwerk unterbrechen kann.
    
- Stern
    
    Bei der Sterntopologie sind die Netzwerkteilnehmer mit einem zentralen Verteiler (Router / Switch) verbunden. Dieser Verteiler ist der Schwachpunkt des Netzwerks. Zusammen mit der Baumtopologie ist die Sterntopologie eine der beliebtesten heutzutags.
    
- Baum
    
    Ein Baumnetzwerk ist der Zusammenschluss mehrerer Sternnetzwerke. Baum- und Sternnetzwerk sind die heutzutags meist benutzten Topologien (wird zB. auch in der GIBB genutzt).
    
- Bus
    
    Bei einer Bustopologie sind mehrere Netzwerkteilnehmer aneinandergeschalten und mit einer gemeinsamen Leitung verbunden. Das wird heutzutage meist nicht mehr gemacht, da es sehr komplexe Timings braucht - keine zwei Teilnehmer dürfen gleichzeitig Daten auf den Bus senden
    

## Vor&Nachteile

- ->Punkt zu Punkt
+Direkte Verbindung aller Netzwerkteilnehmer
-Teure Verkabelung mit viel Arbeitsaufwand
- ->Ring
+Hohe Ausfallsicherheit
-Hoher verkabelungsaufwand
-Einzelner Ausfall schwächt Gesamtnetz
- ->Stern
+Einfache verkabelung, relativ wenig Arbeitsaufwand
+Leicht erweiterbar
-Router ist die Schwachstelle / Single point of failure
- ->Baum
+Leicht erweiterbar
-Viel Verkabelungsaufwand
- ->Bus
+Einfache Installation
+Geringe Kosten
-Netzausfall wenn Bus kaputt
-Begrenzte Leistungslänge

# Netzwerkausdehnung

Es gibt verschiedene Netzwerktypen, wie auch schon im BBC drankam;

## Pan / WPAN

Das Personal area network besteht meistens nur aus zwei Komponenten wie zum Beispiel UE BOOM und Handy. Beim IoT gibt es auch häufig PANs.

## LAN / WLAN

Local are networks sind die Art von Netzwerk, mit der man im Alltag am häufigsten in Berührung kommt. Es hat mindestens ein paar verbundene Maschienen in einem LAN und umfasst höchstens ein ganzes Gebäude oder einen Gebäudekomplex. Mehrere LANs lassen sich zu einem MAN  (Metropolitan Area Network) verbinden.

## CAN

Ein CAN (Campus Area Network) ist ein geografisch limitiertes Netzwerk, ähnlich wie ein MAN

Der Unterschied zu einem MAN ist, dass es meist keine ganze Stadt verbindet, sondern nur einen relativ kleinen Bereich von vielleicht ein paar Häusern. (5km Reichweite)

## WAN / MAN

Wide Area bzw. Metropolitan Area Networks sind Netzwerke, die einen grossen Bereich abdecken. Sie werden meist von Netzprovidern betrieben und versorgen eine Region mit Internet.

## Internet / GAN

Das Internet (man könnte es auch Global Area Network nennen) ist aus fast unendlich vielen WANs zusammengesetzt.

# Schichtenmodelle

Es gibt, wie schon im BBC drankam, mehrere verschiedene Schichtenmodelle, die alle den Datenstrom im Internet auf verschiedenen Schichten (von Applikation bis Kabel) erklären.

![Untitled](Schulmodule/M117%20-%20Netzwerke/Fotos%20&%20PDFs/Untitled.png)