#schule 
#m114


# Lernziele

- Den Unterschied zwischen Bitmap- und Vektorgrafiken erklären.
- Darlegen, wie SVG-Grafiken aus Scripts aufgebaut werden
- Selber einfache Grafiken in Form eines SVG-Scripts erstellen

# Vektorgrafik vs. Bitmap

.svg-Dateien (Scalable Vector Format) erlauben es, nur die Anleitung zum Zeichnen von Linien zu speichern - nicht die Linien ansich. 

# Aufbau einer. svg-Datei

![Untitled](Untitled%2012.png)

- <svg> beschreibt die Zeichenfläche sowie auch den Anfang und das Ende der Datei
- <path> beschreibt die Linie und wie sie gezeichnet wird
    - d setzt den Stift aufs “Papier”
    - M bewegt den Cursor zum Startpunkt
    - L zieht eine Linie zum nächsten Punkt
- *fill* beschreibt, wie eine Grafik ausgemalt werden soll
- *stroke* definiert die Farbe, mit der Gemalt wird

# Vorteile vektorbasierter Grafiken

## Skalierbarkeit

Durch die neuberechnung solcher Grafiken können sie beliebig vergrössert oder verklienert werden. Es wird immer in optimaler schärfe dargestellt.

## Dateigrösse

Da .svg-Dateien nicht individuelle Pixel speichern müssen, sind die Häufig effizienter in der Speichernutzung als ihre auf Pixel basierenden Kollegen.

# Nachteile vektorbasierter Grafiken

Vektorbasierte Grafiken sind nicht für komplexe Bilder mit grosser Farbvielfalt und unklaren Konturen geeeignet. Bestimmte grafische Stile lassen sich nur schwer mit ihnen reproduzieren.

# Tools um Vektorgrafiken zu zeichnen

[W3Schools online HTML editor](https://www.w3schools.com/graphics/tryit.asp?filename=trysvg_path)

# Vektorgrafiken generieren

## Der “Circle”-Befehl

Mit diesem Befehl kann man Kreise und Ellipsen ezeugen.

`<circle cx="69" cy="420" r="4269" stroke="black" stroke-width="1" fill="blue" />`

- cx ist  die X-Koordinate des Mittelpunkts
- cy ist die Y-Koordinate des Mittelpunkts
- r ist der Radius

## Der “Path”-Befehl

Mit diesem Befehl kann man eine Verbindung zwischen einem oder mehreren Punkten herstellen. Dieser Befehl ist in der oben stehenden “Aufbau eine .svg-Datei” dargestellt.

Der “Path”-Befehl hat eine Reihe von möglichen Linienoptionen, die die grafische Darstellung spezifizieren:

- L → Lineto
- M → Moveto
- C → Curveto
- S = Smooth Curveto
- Q = Quadratic Bezier Curve
- A = Elliptical Arc
- Z = Closepath

GROSSGESCHRIEBENER BUCHSTABE → Absolute Koordinaten

KLEINGESCHRIEBENE BUCHSTABEN → Relative Koordinaten bezogen auf die Cursor-Position.