#schule 
#m122

# Ziele & Anforderungen

- Sie erkennen Automatisierungspotenziale im Umfeld der Systemadministration
- Sie können ein Script ausführen und editieren
- Sie können Anforderungen für die praktische Arbeiten formulieren
- Sie können Ablaufdiagramme lesen und selbst einfache erstellen

# Grundlagen der Softwareentwicklung

(Herdt Campus Verlag - Programmierung Grundlagen mit Python)

## Modularität

Modularität besagt, dass eine Gesamtaufgabe in einzelne Teilaufgaben zerlegt wird. Dadurch wird die Komplexität reduziert und die Verständlichkeit erhöht. Die Module werden über eine Schnittstelle verbunden. 

## Abstraktion

Abstraktion ist die Auswahl relevanter Informationen aus einer grösseren Menge von verfügbaren Informationen.

## Top-Down-Methode

Bei dieser Methode wird ein Programm in Teilprogramme zerlegt. Sind diese noch zu komplex, kann man sie in noch kleinere Teilprogramme aufteilen.

## Bottom-up-methode

Dieser Methode baut zuerst einzelne Module bzw. Teilprogramme, die später zu einem grossen Programm zusammengefügt werden.

Das Problem dieser Methode ist, dass das Zusammensetzen der Module zu Problemen führen kann. 

Bottom-Up wird angewendet, wenn die Aufgabenstellung nicht exakt beschrieben ist und die Details sich noch ändern können.

## Up-Down-Methode (Gegenstromverfahren)

Hier wird die Gesamtaufgabe durch die Top-Down-Methode verfeinert und Teilaufgaben werden bottom-up abstrahiert. Auf diese Weise können kritische Teilaufgaben zuerst getestet werden.

## Software-Lebenszyklus (Phasen)

### Analysephase

In der Analysephase wird definiert, was die Software tun soll. Dazu gehört u.a. der Funktionsumfang, art der Benutzeroberfläche oder was für Software zum Erstellen des Programms genutzt werden soll.

### Entwurfsphase

Hier wird definiert, wie die Software zu realisieren ist. Mithilfe der Top-Down-, oder der Bottom-Up-Methode wird die Grundstruktur der Software ermittelt. Auch Algorithmen werden in dieser Phase festgelegt.

Natürlich kommt man nicht beim ersten Mal auf die finale Version Aus diesem Grund unterscheidet man zwischen Grobentwurf, Feinentwurf und Implementationsentwurf.

### Impementierungsphase

In dieser Phase wird der Code geschrieben. Dazu werden die Module der Entwurfsphase in einer bestimmten Programmiersprache implementiert.

### Integrationsphase

In der Integrationsphase werden die Teilaufgaben zusammengefügt. Ausserdem werden Tests durchgeführt, die die Zusammenführung prüfen.

### Einsatz- und Wartungsphase

In diesen beiden Phasen wird die Software fertiggestellt, vom Kunden abgenommen und es werden schlussendlich auftretende Fehler korrigiert.

## Vorgehensmodelle

Es gibt eine Reihe von Vorgehensmodellen, die die oben beschriebenen Phasen auf unterschiedliche Weise bewältigen.

### Das Wasserfallmodell

Beim Wasserfallmodell sind die Phasen stufenartig angeordnet. Am Ende jeder Phase steht ein Teilprodukt, das in der nächsten Phase weiterentwickelt wird.

Vorteil des Wasserfallmodells ist der geringe Managementaufwand und die leichte Verständlichkeit. Nachteil ist vor allem die geringe Flexibilität, die durch die strenge Reihenfolge der Phasen entsteht.

![Wasserfallmodell](Schulmodule/M122%20-%20Systemadministration/Fotos%20&%20PNGs/Untitled.png)

Wasserfallmodell

### Das V-Modell

Beim V-Modell gibt es nicht eine Testphase, denn jede Phase bekommt ihre eigene Testphase. So wird im Einzelnen jedes Detail- und im Gesamten auch das volle System getestet. 

![V-Modell](Schulmodule/M122%20-%20Systemadministration/Fotos%20&%20PNGs/Untitled%201.png)

V-Modell

Der Voteil dieses Modells ist, dass es sich gut für grosse Projekte eignet und die Qualitätssicherung ein hauptsächlicher Teil des Modells ist. Nachteil dieses Modells ist die aufwändige Verwaltung und dass es für kleine Projekte nicht geeignet ist. Dafür ist der Aufwand mit den ganzen Zwischenprodukten zu gross.

### Das Prototyping-Modell

Bei diesem Modell wird zunächst ein Prototyp entwickelt, der als erste Version des Produkts verwendet wird. Ein guter Prototyp kann zu einer besseren Version weiterentwickelt werden.

Bei Prototypen wird zwischen vertikalen und horizontalen Prototypen unterschieden. Horizontale Prototypen implementieren eine Ebene vollständig (zB. UI/UX), aber ohne Funktionalität. Vertikale Prototypen besitzen vollständige Funktionalität, aber nur für einen Teil des Systems.

![Darstellung vertikaler und horizontaler Prototypen](Schulmodule/M122%20-%20Systemadministration/Fotos%20&%20PNGs/Untitled%202.png)

Darstellung vertikaler und horizontaler Prototypen

### Das Spiralmodell

Das Spiralmodell ist eine Vereinigung von dem linearen Wasserfallmodell und dem evolutionären Prototypmodell. Es wird heutzutags häufig verwendet.