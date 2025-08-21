#ÜK
#betriebssysteme
# Lernziele Betriebssysteme und Bootvorgang

- Kennt Aufgaben, Aufbau und Komponenten eines Betriebssystems und kann damit die unterschiedlichen Grundkonzepte und Merkmale von Betriebssystemen erläutern
    - Aufgaben eines Betriebssystems sind I/O, Ausführen von Programmen, Verwaltung der Prozessorzeit, Arbeitsspeicher und angeschlossene Geräte.
    - Komponenten eines Betriebssystems:
    
    ![Untitled](ÜK/ÜK%20Betriebssysteme/PDFs&Fotos/Untitled.png)
    
    - Grundkonzepte von Betriessystemen:
        - System Call → Aufruf einer Anwendung an das Betriebssystem (Datei öffnen / Befehl ausführen). Fast jeden Input, den ein User macht, löst im Hintergrund mehrere System Calls aus.
        - Multitasking → Gleichzeitiges aufsühren mehrerer Programme bzw. Prozesse. Auch Multithreading genannt.
        - Multiuser → Gleichzeitiges Benutzen der Hardware durch verschiedene User.
    - BIOS-Zweck → Das Bios hat den ersten Code, der nach einem Kaltstart auf dem Computer läuft. Es lädt den Code des Betriebssystems zum Arbeitsspeicher/CPU, damit dieses starten kann.
- Kennt die Vorbereitungsschritte, welche vor der Installation des Betriebssystems zu treffen sind und kann erläuftern, wie diese zu einer erfolgreichen Installation beitragen

### Bios

- Verwendet MBR
- Älteres System, UEFI ist neuer
- Limitierter Hardware-Support

### UEFI

- Nachfolger von BIOS
- Benutzt GPT
- Für neuere Hardware gemacht
- Ist unsicherer, da es vor dem Start des Betriebssystems auf das Internet zugreifen kann

### Bootloader

- Erstes Programm, das nach BIOS / UEFI gestartet wird. Startet das OS, bzw. lässt den User zwischen mehreren OS’ entschieden, wenn es ein Bootmanager / Dual-Boot ist.

### Bootvorgang BIOS

1. POST (power-on-self-test)
2. BIOS Bootreihenfolge auslesen
3. MBR des Bootdatenträgers
4. Stage 1 des Bootloaders
5. Stage 2 des Bootloaders (bzw. Bootmanagers)
6. Start von Windows (-Kernel) 

# Lernziele Partitionen und Dateisysteme

### Partition Definition:

Eine Partition teilt eine Festplatte in Teile bestimmter Grössen auf. Jeder dieser Teile hat ein eigenes Dateisystem, welches unabhängig vom Rest des Datenträgers fungiert. 

### Ziele

- Datenträger-Partitionen und Dateisysteme einrichten, Bootmanager und Bootoptionen konfigurieren
- Datei- und Verzeichnisstukturen aufbauen und verwalten
- Kennt die technischen Rahmenbedingungen einer Partitionierung und wie diese bei der Installation zu berücksichtigen sind.
- Kennt die wichtigsten Datenträger-Verwaltungsstruktuern (MBR/GPT, Partitionstabelle, Bootrecord, Bootloader), die für das Booten notwendig sind, und welche Aufgaben diese in den einzelnen Stufen des Bootvorgangs ausüben.
    - MBR → Älteres Partitionsschema, welches nur 4 primäre Partitionen mit einer max. Grösse von 2TBs unterstützt.
    - GPT → Neueres Partitionsschema, unterstützt 128 Partitionen mit je 18 ExaByte!
- Kennt Eigenschaften und Kompabilität der gängigen Dateisysteme und welche Vor-, Nachteile sowie Einsatzgebiete daraus resultieren.
    - FAT32 → Win / Linux / Mac
        - Kompatibel mit allen Betriebssystemen
        - Max. Dateigrösse 4GB
    - NTFS → Win only
        - Von Microsoft erstellt, sehr eingeschränkt für andere Betriebssysteme
    - exFAT → Win / Linux / Apple
        - Erlaubt das setzen von Rechten
    - ext4 → Fourth extended filesystem
        - Standart auf vielen Linux-Distros
    - APFS
        - Standart für Apple-Systeme
        - Für SSDs optimiert
- Kennt die unterschiedlichen Konzepte für den Zugriff auf Datenträger und Dateisysteme (zB. Mount-Befehl, Devicedateien, Treiber) sowie die dazugehörigen Systembefehle und Hilfsprogramme.
    - Auf Windows bearbeitet man Partitionen mit der Computerverwaltung→Datenspeicher→Datenträgerverwaltung
    - Partitionen werden in Windows als Laufwerke dargestellt