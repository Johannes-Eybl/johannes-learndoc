#programming
Es folgen die wichtigsten Stichpunkte, die man für ein Refactoring beachten muss

- STATIC Funktionen sind, diejenigen, die keine Instanzvariabeln brauchen
- KONSTANTEN haben *final* und *static*

# Codebewertung BBC

- Durchdachte Ordnerstruktur (Packages), sinnvolle Datei-/Ordnernamen
- Code ist sinnvoll in Klassen aufgeteilt (mit Vererbung und abstrakte Klassen)
- Sichtbarkeitsmodifikatoren werden richtig eingesetzt (*private, public, protected*)
- Keine Redundanzen → Don’t Repeat Yourself
- Sinnvolle Namensgebung von Klassen, Methoden und Variabeln. Sprachspezifische Konventionen werden eingehalten.
- Einheitliche Formatierung
- Kein auskommentierter Code
- Sinvolle und einheitliche Klassenstrukturen
- Keine unnötigen Leerzeilen
- Nicht selbsterklärende Codezeilen sind kommentiert

# Clean Code references

- [Single level of abstraction](https://www.google.com/search?client=firefox-b-d&q=single+level+of+abstraction)
- [Divide and Conquer](https://www.google.com/search?client=firefox-b-d&q=divide+and+conquer)
- [Model-View-Controller](https://www.google.com/search?client=firefox-b-d&q=mvc#vhid=ZGrlIqnbAhYrhM&vssid=l)
- [Model-View-Viewmodel](https://www.google.com/search?client=firefox-b-d&q=mvvm#vhid=94pocVXbG7HQkM&vssid=l)
- [Fat model, skinny Controller](https://www.google.com/search?client=firefox-b-d&q=skinny+controller+fat+model)

[https://clean-code-developer.com](https://clean-code-developer.com/grades/grade-5-blue/)
# Seperation of Concerns

Code der allgemein nutzbar (nicht Projektspeziefisch) ist, kann in normale Ordner ausgelagert werden. Genau so kann man Code, der sich um bestimmte Teile des Programms kümmert, in andere Ordner/Packages auslagern

# Divide et impera

Jede Klasse muss genau eine Aufgabe haben. 

Alle Methoden und Variabeln stehen mit dieser Aufgabe in Verbindung.

# Kapselung

Eine Klasse sollte ihre Methoden und Variabeln von anderen Klassen abkapseln

Darum viel mit *private* und *protected* arbeiten. *public* nur nutzen wenn umbedingt notwendig.

# Do One Thing

Eine Methode soll nur etwas machen. Der Methodenname muss ein Verb sein, das die Aufgabe beschreibt.

# Don’t repeat yourself (DRY)

Redundanz vermeiden und reduzieren

# Magic Numbers

Zahlen im Code, deren Bedeutung nicht unmittelbar erkennbar ist, als Konstanten iniziieren.