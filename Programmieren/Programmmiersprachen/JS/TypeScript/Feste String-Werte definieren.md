#typescript 
#programming 
Wenn man will, dass eine Variabel nur bestimmte Strings enthalten darf (zb. 'offline' und 'online'), kann man diese bei der Erstellung der Variabel festlegen:
```TypeScript
let state: 'offline' | 'online' = 'offline'
```
Will man diese Variabel nun auf etwas anderes als die zwei vordefinierten Strings setzen, gibt es einen Error.