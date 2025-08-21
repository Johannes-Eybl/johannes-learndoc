# Macro Erstellen
Es folgt eine Zusammenfassung des Atlassian-Tutorials zu Macros. 

### 00 - Plugin-Skelett erstellen
Zunächst muss ein Plguin-Skelett erstellt werden. Dies wird mit dem Befehl `atlas-create-confluence-plugin` umgesetzt.
### 01 - `atlassian-plugin.xml` erweitern
Für ein Marco muss in der Datei `atlassian-plugin.xml` nach dem `</web-resource>`-Tag der folgende Codeblock eingefügt werden:

```xml
<xhtml-macro name="helloworld" class="com.atlassian.tutorial.macro.helloworld" key='helloworld-macro'>     
	<description key="helloworld.macro.desc"/>     
	<category name="formatting"/>     
	<parameters/> 
</xhtml-macro>
```
### 02 - `myConfluencePlugin.properties` erweitern
Danach muss man die Datei `/src/main/resources/myConfluenceMacro.properties` um die folgende Zeile erweitern: `helloworld.macro.desc="Hello World"`
### 03 - `helloworld.java` erstellen
Zuletzt muss die Datei `/src/main/java/com/atlassian/tutorial/macro/helloworld.java` erstellt werden. In dieser Datei wird der folgende Code rein kopiert:
```Java
package com.atlassian.tutorial.macro;

import com.atlassian.confluence.content.render.xhtml.ConversionContext;
import com.atlassian.confluence.macro.Macro;
import com.atlassian.confluence.macro.MacroExecutionException;

import java.util.Map;

public class helloworld implements Macro {

	public String execute(Map<String, String> map, String s, ConversionContext   conversionContext) throws MacroExecutionException {
        return "<h1>Hello World</h1>";
    }

    public BodyType getBodyType() { return BodyType.NONE; }

    public OutputType getOutputType() { return OutputType.BLOCK; }
}

```
Zuletzt kann das Projekt mit dem Befehl `atlas-mvn package` re-packaged werden.

## Macro - Parameter
Jedes Macro in Confluence kann ein oder mehrere Parameter haben, die die Funktionsweise des Macros verändern - so wie Parameter bei Linux Befehlen.
Parameter werden innerhalb der Datei `atlassian-plugin.xml` definiert. Man kann verschiedene Eigenschaften von Parametern, wie beispielsweise den Namen oder Datentypen definieren. Diese werden dann beim Erstellen des Macros in die `execute()`-Funktion (der Java-Klasse) weitergegeben. 

Der folgende Code definiert zwei Parameter. Einmal ein Eingabefeld namens "Name" und ein Dropdown mit mehreren Optionen:
```XML
<parameters>  
    <parameter name="Name" type="string"/>  
    <parameter name="Color" type="enum">  
        <value name="red"/>  
        <value name="green"/>  
        <value name="blue"/>  
    </parameter>
</parameters>
```