#angular 
#JavaScript 
#frontend 
Anstatt Components als "standalone-components" zu bauen, kann man diese auch als "Module-based-Components" erstellen.

Anstatt in jedem Component zu definieren, welche anderen Components von diesem genutzt werden, kann man ein Modul definieren, welches all diese Components vereint. Dadurch muss man die einzelnen Components nicht so viel konfigurieren, wie es normalerweise der Fall ist.

Ein Modul ist also wie eine Abhängigkeits-Konfiguration für Components. Es definiert, auf was die enthaltenen Components zusammen zugreifen können.

# Module erstellen
```TypeScript
@NgModule({  
  declarations: [AppComponent],  
  bootstrap: [AppComponent],  
  imports: [BrowserModule, HeaderComponent, UserComponent, TasksComponent]  
})  
export class AppModule {  
  
}
```
Jedes Modul hat ein Konfigurationsobjekt (so wie Components auch), welches folgende Attribute enthält:
- declarations -> Welche Components zu diesem Modul gehören. 
- imports -> Welche Standalone-Components zu dem Modul gehören
- bootstrap -> Der Root-Component, den Angular zum Start der Applikation verwendet.

Um neue Abhängigkeiten zu definieren, fügt man diese nun zu den Declarations hinzu. So spart man innerhalb der Components Platz.

> [!WARNING] Module funktionieren am besten mit Non-Standalone-Components!
# Unterschied Standalone- und Module-Based-Components
## Standalone
- Components definieren selbst, welche anderen Components sie verwenden.
- Kein Modul erforderlich
- Abhängigkeiten sind explizit und übersichtlich, müssen aber jeweils einzeln konfiguriert werden
## Module-Based
- Komponenten werden in einem gemeinsamen Modul zusammengefasst
- Abhängigkeiten werden zentral konfiguriert, weshalb nicht sofort ersichtlich ist, was von was abhängig ist.
