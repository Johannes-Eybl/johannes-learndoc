# Drag Events
Ein Drag-Event beginnt, wenn der Nutzer ein Draggable-Element anklickt, geht weiter wenn er es über den Bildschrim zieht und ended, wenn er es loslässt.

| Event     | Wird ausgelöst von                                                                                                            |
| --------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `drag`    | Ein Element wird gedraggt. Triggert jeden Frame                                                                               |
| dragend   | Ein drag-event wird beendet                                                                                                   |
| dragenter | Ein Element wird über ein valides drop-element gezogen (aber nicht losgelassen)                                               |
| dragleave | Ein Element wird von einem validem drop-element weggezogen                                                                    |
| dragover  | Ein Element wurde für kurze Zeig über ein valides drop-Element gezogen. Auch wenn es nur ein paar hundert MIlisekunden waren. |
| dragstart | Ein drag-Event wird gestartet                                                                                                 |
| drop      | Ein Item wird auf einem validen drop target gedroppt                                                                          |
- Wenn ein Element erfolgreich über eine Dropzone gedroppt wird, wird "dragend" UND "drop" aufgerufen. Es wird immer zuerst "drop" und danach "dragend" aufgerufen!