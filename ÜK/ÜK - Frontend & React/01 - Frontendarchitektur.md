#ÜK
#frontend
## Handlungsnotwendige Kentnisse

- Richtet die lokale Entwicklungs- und Laufzeitumgebund so ein, dass ein vorgegebenes Projekt entwickelt werden kann.
    - Kennt die für die Entwicklung zu installierenden Komponenten (also welche Softwarebibliotheken benötigt werden)
    - Kennt Vorgehensweise, um an entsprechende Installationsanleitunge zu gelangen.
- Programmiert mittels vorgegebener Technologie und mit Hilfe eines existierenden, dokumentierten Back-Ends ein effizientes, strukuriertes Front-End einer interaktiven Webapp, welches die Verwaltung (CRUD) von Daten ermöglicht. Hält sich dabei an relevante Vorgaben.
    - Kennt die grundlegenden Prinzipien aktueller Umsetzungsarten für das Front-End einer interaktiven Webapp (zB. Single Page Application mt Javascript oder Typescript)
- Legt Änderungen und Erweiterungen der Implementierung übersichtlich und zuverlässig in einem Softzwareverwaltungssystem ab.
    - Kennt die grundlegende Bedienung und den Workflow einer Softwareverwaltungssystems.

## Lernziele

- Du kannst die drei vorgestellten Webarchitekturen erklären
- Du lernst die JS Library react.js kennen
- Du lernst das JS Framework next.js kennen
- Du kensnt die Programme node und npm

## Klassische Architektur

1. Request von Client zu Server mit einem URL-Aufruf
2. Der Server sendet dann ein Datenpaket mit HTML, CSS und weiteren Content an den Client
3. Wenn der Client wo klickt, wird die *gesamte* Seite wieder an den User gesendet

## Moderne Architektur mit Rest API und Single Page Applikation

Bei der modernen Architektur mit der Rest API wird zunächst nur das nötigste geladen (das Grundgerüst wie index.html) und erst danach sendet der Server den Content nach. So kann eine Mobile-App die selben Daten verwenden. Ein einziger Server kann die Daten zur Verfügung stellen.

## Server Side Rendering

Beim Server Side Rendering tut der Server die erste Version von HTML und CSS liefern und danach Dinge wie Content oder JS senden. Es ist eine Mischung aus der Klassischen Architektur und der der Single Page Application. “Das beste aus beiden Welten” - Mark

## Components

Frontend Apps bestehen aus Komponenten. Diese Komponenten können so gross wie eine ganze Seite oder so klein wie ein einzelner Knopf sein. Komponenten können verschachtelt werden. Ein Komponent ist Teil des UI der über eine eigene Logik und ein eigenes Erscheinungsbild (CSS) verfügt.

## React.js

Ist eine Library, mit der man Komponenten entwickelt. Komponenten werden als “html in js” geschrieben.