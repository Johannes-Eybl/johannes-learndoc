#programming 
#springBoot
#java
Diese Klasse enthält Rest-Endpunkt. Mit der Annotation ```@RequestMapping("/beispiel")``` wird die URI des Controllers definiert (zb. "/items" und "/persons")

```Java
@RestController
@RequestMapping("/beispiel")
public Class BeispielController{

}
```
# Funktionen mappen
Mit ```@GetMapping```,  ```@PostMapping```,  ```@PatchMapping``` und  ```@DeleteMapping``` wird die http-Methode mit einer Funktion verbunden. Funktionen, die auf http-Methoden gemappt sind, müssen immer eine ```ResponseEntity<?>``` zurückgeben.
```Java
@GetMapping("/")  
public ResponseEntity<?> sayHello() {  
    return ResponseEntity.ok("<h1>Hello World!</h1>");  
}
```

# Service einbinden
Der [[Service]] (die zweite Schicht der [[Architektur]]) wird im Konstruktor eingebunden:
```Java
@RestController
@RequestMapping("/beispiel")
public Class BeispielController{
	private final BeispielService beispielService;

	@Autowired
	public BeispielController(BeispielService beispielService){
		this.beispielService = beispielService;
	}

}
```
# Übergabe von Parametern
## @PathVariable
Variablen aus dem *Pfad* "/beispiel/1"
```Java
@GetMapping(path="{id}")
public ResponseEntity<?> findById(@PathVariable Integer id)
```
## @RequestParam
Variablen mit http-GET "/beispiel?name=foo".
Kann default Wert definieren.
```Java
public ResponseEntity<?> findItems(@RequestParam(required=false) String name)
```
## @RequestBody
Variablen mit http-POST/PATCH - Daten kommen aus dem Body.
```Java
public ResponseEntity<?> insert(@RequestBody ItemRequestDTO item)
```