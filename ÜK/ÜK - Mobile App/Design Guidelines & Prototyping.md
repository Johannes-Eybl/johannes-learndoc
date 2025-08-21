#ÜK
#mobileApp
# Ziele

- Wissen, das Prototyping ist
- Wissen, was ein Wireframe ist
- Wissen, welche Design Guidelines es gibt
- Wissen, was bei verschiedenen Bildschirmgrössen beachtet werden muss
- Wissen, nach welchen Vorgaben der Prototyp bewertet wird

# Die verschiedenen Stadien im Prototyping

1. Scribbles → einfache Skizzen
2. Wireframe → Digitaler Entwurf. Ohne Farben, Schriften & Bilder. Dient als Diskussionsbasis
3. Mockup → Vorführmodell. Erste Use-Cases werden durchgespielt. Enthält Farben, Text und Bilder.
4. Prototyp → Kommt dem finalen Produkt sehr nahe. Klickbar und interaktiv.

# Wireframes

Die Idee hinter Wireframes ist, dass noch viel verändert und ausprobiert werden kann. 

Verschiedene Dinge wie Grösse der Elemente und Positionierung der Komponenten.

# Bildschirme

Die wichtigsten Eigenschaften von Bildschirmen sind: Auflösung, Ausrichtung und Grösse.

## Auflösung

Die Auflösung des Bildschirms beeinflusst, ob Schriftgrösse und Bilder gut aussehen.

React Native hat `PixelRatio`, mit der man das Pixelverhältnis auslesen kann.

## Bildschirmdichte

Das Koordinatensystem von React Native basiert auf density independent Pixels (dp). 

Mit dp kann man gut einschätzen, welche Grösse Elemente haben.

Damit aber bei allen Auflösungen die gleichen Dimensionen verwendet werden, muss man `PixelRatio` verwenden!

