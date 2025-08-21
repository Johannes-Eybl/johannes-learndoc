#linux
# Basics
Wenn man mit `:` einen Befehl schreibt, kann man `ctrl-D` drücken, um mögliche Befehle zu sehen

- Characters löschen mit `x`. Löscht den Char rechts vom Cursor
- Undo last command with `u` and whole Line with `U` (wie ctrl-z)
- Redo Commands with `ctrl r`
- Gelöschten Text einfügen mit `p`
- Normale Shell-Befehle auslösen mit `:![BEFEHL]`

# Navigation

- Cursor-Movement mit h,j,k,l
- Sprung zu Anfang der Datei mit `gg` , Ende der Datei mit `G`
- Sprung zu bestimmter Zeile mit `[ZEILEN-NR] G`
- Aktuelle Zeile ausgeben mit `ctrl G`

# Inserting Text

- Characters einfügen mit `i [EINGABE]`. Zurück zu Navigation mit `esc`
- Characters appenden (anschliessen?) mit `a [EINGABE]`. Zurück zu Navigation mit `esc`
- Characters am Ende der Zeile mit `A` appenden
- Characters mir `r` ersetzten. Funktioniert nur einen Char at a time. Mit `R` bleibt man im replace-mode, bis man `esc` drückt
- Auf neuer Zeile (unter Cursor) schreiben mit `o`
- Auf neuer Zeile über dem Cursor schreiben mit `O`

# Exit and Save

- Exit&no save: `esc :q! enter`
- Exit&save: `esc :wq enter`
- Save to new File: `:w [FILENAME]`  → Saves to current Dict

# Visual Selection

`v` beginnt die Auswahl an der Stelle, wo der Cursor ist. So lange ein Teil des Textes Ausgewählt ist (in Weiss), kann man mit normalen Befehlen nur diesen Teil des Textes bearbeiten. (Zb. mit `w[NAME]`,was nur den Ausgewählten Text in eine neue Datei speichert. Oder `d` würde den Text löschen.)

# Copy & Paste

- Mit `y` kopiert man und mit `p` fügt man ein
- Man kann die Copy&Paste-Befehle mit Motions ergänzen um zu entscheiden, was kopiert wird. Zb. `yy` kopiert die ganze Zeile, `yw` kopiert ein Wort
- Am einfachsten ist es, bereits mit `v` ausgewählten Text zu kopieren.

# Retrieving

- `:r [FILENAME]` setzt den Inhalt der gewählten Datei an die Position des Cursors
- `:r ![BEFEHL]` setzt den Output eines Shell-Commands an die Position des Cursors

# Search Command `/` und `%`

- Mit `n` und `N` kann man zwischen Suchergebnissen hin- und her springen
- Mit `ctrl o` kommt man zur Stelle zurück, wo der Cursor zuletzt war
- Der `%` Command wird bei Parentheses angewendet (Klammern wie [],{} oder ()), um die zugehörige schliessende Klammer zu finden

# Substitute/Search&Replace Command `s`

- `:s/oldstring/newstring`       → Ändert das erste Vorkommen von oldstring nach der Position des Cursors
- `:s/oldstring/newstring/g`    **→** Wie search and replace bei Word, ändert jeden oldstring in der Zeile wo der Cursor ist
- `:#,#s/oldstring/newstring/g` → Ändert jeden oldstring zwischen Zeile # und '#s'
- `:%s/oldstring/newstring/g` → Ändert jeden oldstring in der Datei

Man kann anstatt `g` auch `gc` schreiben, dann fragt es vor jeder Änderung nach Erlaubnis.

# Delete-Operator `d`

**d _number_

- Wort löschen mit `dw` (delete word)
- Zeile vom Cursor an löschen mit `d$`
- Ganze Zeile löschen mit `dd`

# Change-Operator `c`

**c _number_ 

- Characters bis zum Ende des Wortes ersetzen mit `ce` . Der Befehl löscht das Wort ab der Position des Cursors und setzt dich in den Insert mode.
- Characters bis zur Ende der Zeile ersetzen mit `cc`

# Motions

Motions sind shortcuts, mit denen man den Cursor direkt an bestimmte Stellen im Text bewegen kann. Man kann Motions auch mit Nummern verbinden, um einen Befehl x mal zu wiederholen, zb `3e` bewegt den Cursor zum drittnächsten Wort.

- zum Anfang des nächsten Wortes mit `w`
- Cursor zum Ende des jetzigen Wortes mit `e`
- zum Ende der Zeile mit `$`
- zum Anfang der Zeile mit `0`

Mit einer Kombination von Motion- und Zahl kann man komplexe Befehle eingeben. Zum Beispiel Löscht `d3w` die nächsten 3 Worte von der Position des Cursors aus gesehen.