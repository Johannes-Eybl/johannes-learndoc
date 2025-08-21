# Was ist 'Processing'
Processing ist ein Framework, welches für grafische Spielereien entwickelt wurde. Es kann 2- und 3-Dimensionale Grafiken erstellen. Unterstützte Programmiersprachen sind Java, Python, JS und ein paar andere. Da Processing auf JavaFX basiert, wird aller Code schlussendlich zu Java übersetzt. Trotz dieser Basis werden keine GUI-Elemente unterstützt. 
# Setup
```python
# 'main methode'
def setup():
	# Window Grösse einstellen
	size(800, 600)

	# Kreis zeichnen
	# circle(xCoord, yCoord, durchmesser)
	circle(200, 300, 50)

	# Viereck machen
	square(50, 50, 50)
```

# Koordinatensystem
Der Nullpunkt ist oben Links. Im Gegensatz zu Godot gehen Y-Koordinaten von Oben nach Unten ins Positive.

# Rendering

