#ÜK
#frontend

# Lernziele

- Du lernst React kennen
- Du kannst mit JS und JSX im DOM anzeigen
- Du kannst eigene Components definieren und mit React darstellen
- Du weisst, wie du mittels Props Argumente an deine Components übergibtst

Mit React kann man HTML-Elemente wie zB. den Header in verschiedene Elemente aufteilen und diese in verschiedene Dateien auslagern. Diese Elemente können dann importiert werden

# Components

Mit JavaScript und JSX werden Components definiert. Diese Components sind html-Blöcke und können wie Html-Tags aufgerufen werden. *Components werden immer gross geschrieben.*

Wenn ein Teil der Webseite verändert werden muss, wird nur der einzelne Komponent verändert. Das erhöht die Wiederverwendbarkeit dieser Komponenten.

# Layout Dateien (/_app.js)

Der App-Component wird von next.js als Rootcomponent genutzt (vergleichbar mit der *main* methode eines Java-Programms). Alles, was in der *App*-Methode eingefügt wird, ist auf allen Seiten sichtbar. 

Diese Datei enthält also “Grundgerüst”-Components, welche mehrmals verwendet werden können (zB. der Header). 

- Layout-Dateien haben immer einen Unterstrich am Anfang vom Namen
- Layout-Dateien haben immer einen *Component*-Tag, welcher die aufgerufene Seite repräsentiert. Diese Tag wird also mit dem entsprechenden html gefüllt

# Props

### Was sind Props

Da jeder Component eine Funktion ist, kann man diesen auch Argumente übergeben. Diese Argumente nennt man *Props*. Es wird immer nur ein Prop übergeben, welcher ein JS-Objekt ist. 

### Wie man Props definiert

So wie man beim Nutzen eines Tags seine Werte definiert (zB. dem *a* Tag einen Link gibt), kann man beim Einsatz der eigenen Components ihnen ihre Props mtgeben. 

### Einfache(re) Nutzung von Props

Da die verschiedenen mitgegebenen Werte innerhalb eines Objekts bzw. eines Arguments zusammengefasst werden, enstehen komische Umstände, bei denen man sich immmer wieder auf das eine Objekt beziehen muss. Mit *destructuring* kann man dieses Objekt entpacken und die einzelnen Variabeln direkt ansprechen.