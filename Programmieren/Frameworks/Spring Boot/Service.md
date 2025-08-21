Der Service ist die mttlere Stufe der [[Architektur]].
# Einbinden
Um die Daten aus einem [[Repository]] zu [[DTOs]] zu machen, muss man das Repository in einem Service einbinden. Dies geschieht im Konstruktor mit der Annotation '@Autowired'.
```Java
@Service  
public class ItemService {  
    private final ItemRepository itemRepository;  
  
    @Autowired  
    public ItemService(ItemRepository itemRepository){  
        this.itemRepository = itemRepository;  
    }
}
```
Nun ist das Repository verbunden und kann innerhalb vom Service verwendet werden.
