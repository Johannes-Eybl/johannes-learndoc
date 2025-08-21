#ÜK
#frontend
# Lernziele

- Du lernst den Begriff “Hook” kennen
- Du kannst deine Components mit Eventhandlern interaktiv machen
- Du verstehst, wie du deinen Components einen *State* (innerern Zustand) geben kannst mittels dem *useState* Hook

### Kurze overview functional Programming

“Pure Functional” - bedeutet, dass die Komponente von nichts abhängig ist, ausser ihrem Input. Vergleichbar mit einer Mathematischen Funktion, die einen Input bekommt, von dem ihr Output abhängig ist.

# “useState()”

Diese Funktion wird verwendet, um sich verändernde Daten zu verarbeiten. Der *Hook*, also diese Funktion, nimmt ein optionales Argument - den default bzw. initial State.

Die Funktion gibt ein Array mit zwei Werten zurück. Die Value und der Setter. Die Value kann innerhalb des Html’s verwendet werden und wenn es sich verändert, wird auch das Html beim Nutzer geupdatet. Das zweite Element im Array ist eine Setter-Funktion für das erste Element.

Dadurch kann sich ein Element dynamisch (zB. als Reaktion auf nen Knopfdruck) verändern.

Managed Inputs → Inputs, die von React gemanaged werden

Unmanaged Inputs → Inputs, die *nicht* von React gemanaged werden