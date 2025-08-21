#programming 
#springBoot
#java
# Was ist Spring Boot
Spring Boot ist ein Framework für die Entwicklung von Webanwendungen.

Spring Boot funktioniert nach dem Prinzip "Convention over Configuration" - das bedeutet, dass man möglichst wenig konfigurieren muss bzw. möglichst viel "out of the box" funktioniert. 

Zusätzlich bietet Spring Boot einen eigenen HTTP-Server, sodass man diesen nicht selber installieren und konfigurieren muss.

> [!NOTE] Spring Boot ist self-contained
> Das bedeutet, dass man keine zusätzlichen Programme oder Tools installieren muss, um ein Projekt zum laufen zu bringen!

# Spring Boot und Spring
Spring Boot benutzt Spring im Hintergrund. Es vereinfacht die Nutzung von Spring durch die Automatisierung von anstrengenden Konfigurationen.

Es ist wichtig zu wissen, dass Spring Boot keines der Features von Spring ersetzt! Spring Boot nutzt alle Features von Spring und fügt seine eigenen hinzu!
# Programmieren mit Spring Boot - Annotationen
Spring Boot wird mit Controller-Klassen programmiert, welche mit "@"-Annotationen definiert werden. 
# Spring Initializr
Auf der Website http://start.spring.io kann man schnell und einfach ein Spring Boot Projekt erstellen. Man erhält eine Vorlage für ein Projekt, welche bereits konfiguriert ist und schnell zum laufen gebracht werden kann.
# Spring Boot deployen
Spring Boot-Apps können auch auf einem anderen HTTP-Server deployed werden. Das ist technisch nicht nötig, da sie bereits einen eigenen Server enthalten.
Um Spring Boot auf einem HTTP-Server zu installieren, muss man sein Projekt als WAR-Datei (Web Application aRchive) deployen.