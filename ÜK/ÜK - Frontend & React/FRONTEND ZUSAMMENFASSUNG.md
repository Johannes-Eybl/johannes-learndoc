#ÜK
#frontend
# HTML - Formulare

## Ziele

- HTML-Formulare gestalten
- HTML-Formulare strukturieren

## Was sind HTML-Formulare

Unter “Formulare” fallen alle Tags, die für das Sammeln von Daten der Benutzer genutzt werden. Zb. Checkboxen oder Textfelder.

## HTML-Tags für Formulare

Um in HTML ein Formular zu implementieren, muss man dessen Inhalt in ein  `<form>`-Tag packen. Dieser Tag hat zwei Attribute; `action` und `method`. Diese werden verwendet, um den Input des Users an einen (Javascript- oder PHP-) Script weiter zu leiten. Wie das genau funktioniert, ist im Backend-Modul genauer beschrieben.

Bei User-Input-Tags ist wichtig, dass jedes Tag das Attribut `name` hat. Wenn dieses Attribut fehlt, werden keine Daten gesendet, denn es ist ein Key für den Datensatz

### Textfelder - einzeilig

`<input type="text">` ist der Tag für einzeilige Textfelder. Dieser Tag hat folgende Attribute: 

- id → sollte “type” entsprechen
- name → sollte “type” entsprechen
- type → Mit “type” kann man festlegen, was für eine Art von Input das Feld entgegen nimmt. [Hier hat es eine Liste an Inputtypes](https://www.w3schools.com/html/html_form_input_types.asp). In diesem Fall - also für ein einzeiliges Textfeld - muss man `type="text"` verwenden.
- placeholder → Der Placeholder enhält einen String, der *nur* angezeigt wird, wenn das Label leer ist.
- required → Wenn man bei den Attributen `required` schreibt, ist es nicht möglich das Formular abzuschicken, ohne das Feld ausgefüllt zu haben.

### Textfelder - mehrzeilig

`<textarea>` ist der Tag für grössere Textfelder. Der Tag hat die selben Attribute wie ein normaler `<input>-Tag`. 

### Radiobuttons

Radiobuttons haben folgenden Tag: `<input type="radio">`. Natürlich braucht es noch weitere Attribute, welche bei diesem Tag genutzt werden (*name, value, id…*). 

Man kann, oder sollte, Radiobuttons gruppieren. Dadurch kann immer nur einer der gruppierten Knöpfe ausgewählt werden. Das macht man, in dem man all den Buttons den selben Namen gibt. 

Man kann Radiobuttons auch ein Label geben, das mit dem Attribut `for="xyz"` der Id des Buttons zugewiesen werden kann.

```html
<input type="radio" name="fachrichtung" value="api" id="api">
<label for="api">Applikationsentwicklung</label><br/>

<input type="radio" name="fachrichtung" value="sys" id="sys">
<label for="sys">Plattformentwicklung</label>
```

### Checkboxes

Checkboxen verwenden den `<input type="checkbox">` Tag und haben ansonsten die selben Attribute wie Radiobuttons. 

Wichtig ist, dass bei Checkboxen der *name* mit einem *[]* ergänzt wird. Viele Backend-Tools brauchen dieses Symbol für eine leichtere Verarbeitung.

### Dropdowns

Dropdowns verwenden das `<select>`-Tag, um ein Dropdown zu definieren. Zusätzlich muss ein `<option>`-Tag für jede einzelne Option verwendet werden.

Das *Value*-Attribut muss eindeutig sein, damit es vom Backend verarbeitet werden kann. Zum Beispiel kann man Primary-Keys der Datenbank verwenden.

```html
<select id="music" name="music">
    <option value="0" selected="selected">-</option>
    <option value="1">Elektro</option>
    <option value="2">Klassik</option>
    <option value="3">Pop</option>
    <option value="4">Reggae</option>
    <option value="5">Rock</option>
    <option value="6">Schlager</option>
    <option value="7">Techno</option>
</select>
```

### “Submit”-Knopf

Mit einem *Input*-Tag, dass das Attribut `type="submit"` hat, definiert man den Submit-Knopf des Formulars.