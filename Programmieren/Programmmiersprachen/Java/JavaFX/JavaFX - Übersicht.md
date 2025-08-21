#programming 
#javaFX
#java
# Grundsätzlicher Aufbau

Viele der hier beschriebenen Dinge sind von der [hier](https://www.tutorialspoint.com/javafx/javafx_application.htm) verlinkten Website geklaut.
## Applikation

Die Applikation-Klasse (`javafx.application`) ist der Grundbaustein eines JavaFX-Programms. Es bietet wichtige Funktionen wie zb. solche zum Starten und Stoppen der Applik
ation.

Eine JavaFX-Applikation hat drei Hauptkomponenten - die Stage, die Scene und den Scene Graph mit entsprechenden Nodes.

![Inhalt der Application](Programmieren/Programmmiersprachen/Java/JavaFX/JavaFX%20fotos/Untitled.png)

Inhalt der Application

## Stage

Die Stage-Klasse ist ein Fenster, welches eine *Scene* enthält. Es können aber auch andere Klassen in eine Stage gesetzt werden wie zb. ein *FileChooser* oder ein *DirectoryChooser*. Ausserdem kann die Scene einer Stage gewechselt werden, wie bei einem Theater. ;) 

Die Stage hat zwei wichtige Parameter, `Width` und `Height`. Ausserdem unterscheidet man bei einer Stage zwischen *Content Area* und *Decorations* (Title Bar&Borders).

Dargestellt wird eine Stage, also ein Fenster, mit der `show()`-Methode.

### Arten von Stages

Es gibt folgende Arten, auf die eine Stage dargestellt werden kann:

- [`StageStyle.DECORATED`](https://docs.oracle.com/javase/8/javafx/api/javafx/stage/StageStyle.html#DECORATED) - a stage with a solid white background and platform decorations.
- [`StageStyle.UNDECORATED`](https://docs.oracle.com/javase/8/javafx/api/javafx/stage/StageStyle.html#UNDECORATED) - a stage with a solid white background and no decorations.
- [`StageStyle.TRANSPARENT`](https://docs.oracle.com/javase/8/javafx/api/javafx/stage/StageStyle.html#TRANSPARENT) - a stage with a transparent background and no decorations.
- [`StageStyle.UTILITY`](https://docs.oracle.com/javase/8/javafx/api/javafx/stage/StageStyle.html#UTILITY) - a stage with a solid white background and minimal platform decorations.

## Scene

Die Scene ist die tatsächliche Benutzeroberfläche, welche in einer Stage (also innerhalb eines Fensters) angezeigt wird. Sie enthält all die Elemente, welche dem Nutzer angezeigt werden.

Die Scene ist immer das Kind einer Stage und kann nur bei einer einzelnen Stage vorkommen. 

## Scene-Graph Und Nodes

Jedes Objekt innerhalb einer Scene erbt von der Base-Klasse *Node*. Die Struktur aller Nodes ergibt eine hirarchische Form, die Scene-Graph genannt wird. 

Nodes können UI-Elemente wie Polygone, Buttons oder Bilder, aber auch (!) Container (Parents) wie Groups oder Regions (Chart/Pane/Control) sein.

![Was eine Node alles sein kann (keine Komplettansicht)](Programmieren/Programmmiersprachen/Java/JavaFX/JavaFX%20fotos/Untitled%201.png)

Was eine Node alles sein kann (keine Komplettansicht)

### Arten von Nodes

1. Root Node
    
    Die Root Node ist die erste Node im Scene Tree. Sie wird instanziieren der Scene als Parameter des Szenen-Konstruktors mitgegeben (`new Scene(RootNode);`)
    
    Root Nodes sind immer entweder *Group*, *Region* oder *Webview*. 
    
2. Branch- / Parent Node
    
    Es gibt eine Subkategorie von Nodes, welche Parent-Nodes genannt werden. Diese Nodes enthalten Children und sind immer eine Node der folgenden Kategorien:
    
    - Group → Eine Group enthält eine Liste von Kindern. Diese Kinder werden bei einer Veränderung des Parents (zb. transform, visibility) auch verändert.
    - Region → Regions beinhalten Charts, Controls und Panes
    - WebView → Beinhaltet die WebEngine, ein Mini-Browser für JavaFX. Damit ist es möglich, Websiten innerhalb von JavaFX darzustellen!
3. Leaf Node
    
    Nodes die keine Children haben können (!) sind LeafNodes, zb Bilder, Boxen, Polygone oder Text.
    

# Layout Panes

Layout Panes werden dazu verwendet, Nodes automatisch anzuordnen. Dadurch kann beispielsweise ein GUI automatisch skaliert werden. 

![Untitled](Programmieren/Programmmiersprachen/Java/JavaFX/JavaFX%20fotos/Untitled%202.png)

## HBox und VBox

### Spacing

Spacing definiert den Abstand zwischen Nodes zu einander.

Dem Konstruktor der Box kann ein Spacing mitgegeben werden, welches den Abstand zwischen allen Nodes innerhalb der Box festlegt. → `new HBox(20);`

### Padding

Padding regelt den Abstand von Nodes zu den Rändern des Fensters. Es wird mit der `setPadding()`-Methode das Padding einer Box definiert, konkret sieht das so aus:

`mybox.setPadding(new Insets(123123));`

### Margins

Margins definieren den äusseren Abstand von Nodes. Jeder Node innerhalb einer Box kann ein anderer Margin mitgegeben werden. 

`Hbox.setMargin(button6, new Insets(1,2,3,4));` (top, right, bottom, left)

### Hgrow und MaxWidth/MaxHeight

Mit diesen beiden Elementen ist es möglich, einer Node eine dynamische Grösse zu geben. Sie wird sich also automatisch an den verfügbaren Platz anpassen, bis die MaxWidth/MaxHeight erreicht ist.

`Hbox.setHgrow(button69, Priority.ALWAYS);` (es gibt auch andere Prioritys)

`button55.setMaxWidth(420);` 

Anstatt bei der MaxWidth eine Zahl einzusetzen, kann man auch `Double.MAX_VALUE` verwenden. Das führt dazu, dass sich die Node so weit wie möglich dehnt.

## BorderPane

Beim BorderPane lässt sich jedes Element/jede Node in den Bereich *top, left, right, bottom* und *center* einteilen. Wenn einer der Bereiche keine Nodes hat, wird er nicht dargestellt.

`myborderpane.setTop(button69);`

(Es gibt auch eine Methode `BorderPane.setAlignment()`, welche die Alignments von Nodes innerhalb ihres Bereichs definiert)

![Hier wurde der *buttonLeft* mit der *Pos.CenterI aligned)*](Programmieren/Programmmiersprachen/Java/JavaFX/JavaFX%20fotos/Untitled%203.png)

Hier wurde der *buttonLeft* mit der *Pos.CenterI aligned)*

## FlowPane

Beim FlowPane werden Node hintereinander aufgereit. Wenn in der Breite kein Platz mehr besteht, wird automatisch eine neue Zeile erzeugt.

Im Konstruktor des FlowPanes wird bestummen, ob die Node horizontal oder vertikal angeodnet werden.

`FlowPane pane = new FlowPane(Orientation.HORIZONTAL)`

oder

`FlowPane pane = new FlowPane(Orientation.VERTICAL)`

## TilePane

Beim TilePane werden Nodes in einem Raster plaziert, wobei jedes Element gleich viel Platz einnimmt. Der Inhalt dieser Elemente wird zentriert.

`pane.setPrefTileWidth(100d);` → Setzt die bevorzugte Tile-Breite

`pane.setPrefTileHeight(60d);` → Setzt die bevorzugte Tile-Höhe

`pane.setPrefColumns(2);` → Legt die bevorzugte Anzahl von Spalten fest

## GridPane

Nodes werden vom GridPane in einem Raster (Grid) plaziert. Der Unterschied zum TilePane besteht darin, dasss Spalten unterschiedlich breit sein können.

`pane.setGridLinesVisisble(true);` → Blendet die Grid-Linien ein oder aus

`pane.addRow(0, button69, button420)` → Füge eine spezifische Zeile mit entsprechenden Nodes zum Grid hinzu

`pane.add(button1, 0, 1);` → Fügt eine Node in eine bestimmte Zelle ein (x=0, y=1)

`GridPane.setColumnSpan(button69, 2)` → Macht, dass der *button69* zwei Spalten einnimmt

ColumnConstraints oder auch RowConstraints können Bedingungen für deren Grössen und Ausrichtungen festlegen.

Der folgende Code generiert 2 Columnconstraints, welche gemeinsam eine PercentWidth von 100% haben. Diese werden am Schluss zum Pane addiert.

```java
ColumnConstaints column1 = new ColumnConstraints();
column1.setPercentWidth(40);
ColumnConstraints column2 = new ConlumnConstraints();`
column2.setPercentWidth(60);

pane.getColumnConstraints().addAll(column1, column2);
```

## ScrollPane

Das ScrollPane ist, wie der Name bereits sagt, Scrollbar. In das ScrollPane sollte ein anderes Pane eingesetzt werden.

`pane.setContent(myTilePane);`

# Events

Events sind alle Möglichen dynamischen Dinge, die während der Laufzeit des Programms passieren können. Meistens sind Events Inputs des Users wie Button-Klicks, Keyboard-Inputs oder das betätigen der Scrollbar.

# Canvas

Ein Canvas ist eine Node, die das Zeichnen von Formen, Text und Bildern ermöglicht.

## GraphicsContext

Mit der *GraphicsContext*-Klasse kann man auf den Canvas Formen und Text zeichnen:

`GraphicsContext gc = canvas.GetGraphicsContext2D();`

Folgendes Beispiel zeichnet einen roten Kreis auf den Canvas:

`gc.setFill(Paint.valueOf("#cc0000"));`

`gc.fillOval(50, 60, 300, 290);`

## AnimationTimer

Beim AnimationTimer wird in jedem Frame die *handle()*-Methode aufgerufen. Diese lässt einem eine Animation generieren. Wichtig ist, dass man in jedem Frame den Bildschrim resettet (löscht) und den Inhalt neu generiert.

### Delta

Da PCs keine konsistente Frame Rate haben, muss man die Bewegungen mit dem Delta des Frames multiplizieren. Das Funktioniert genau so wie in Unity oder Godot - das Delta wird der Methode als Parameter mitgegeben.

`public void handle (long actualTime) {}`