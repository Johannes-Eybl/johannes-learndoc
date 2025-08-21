# Wie funktioniert eine Blazor App
Blazor basiert auf dem Web Assembly Standart (WASM). Dieser ist in allen Modernen Browsern implementiert und wird dort genutzt, wo JS auf seine Grenzen stösst (3D, Audio, Video). WebAssembly ist eine Low-Level-Sprache, zu der C#-Blazor -Code übersetzt wird.
# Erstellen eines neuen Projekts
Mit `dotnet new blazor -o PROJEKTNAME` erstellt man das Grundgerüst für ein neues Projekt. 
## Verzeichnisstruktur
- `Program` -> Einstiegspunkt für die App, die den Server startet
- `components/App.razor`-> Root Component der App
- `components/Routes.razor`-> Konfiguriert den Blazor-Router
- `components/Pages/`-> Die Pages der App
- `BlazorApp.csproj`-> Definiert das Projekt und dessen Abhängigkeiten
- `Properties/launchSettings.json`-> Definiert Projekteinstellungen
## App starten
Mit `dotnet watch` kann man die Webseite starten. Sie wird dann automatisch aktualisiert, wenn etwas im Code verändert wird.
# Code
## Beispiel Counter
Ein einfacher Counter als Beispiel. Es wird ein Button und ein Label erstellt. Wird der Button geklickt, geht der Label-Counter um eins hoch.

Immer wenn der Button gedrückt wird, passiert folgendes:
- Das onclick-Event wird ausgelöst.
- Die Methode 'IncrementCount' wird ausgelöst.
- Die Variable "currentCount" wird inkrementiert.
- Der Component wird neu gerendert, um den neuen Count darzustellen.
```c#
@page "/counter"
@rendermode InteractiveServer

<PageTitle>Counter</PageTitle>

<h1>Counter</h1>

<p role="status">Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```
# Components
So wie in React gibt es auch in Blazor Components, die immer wieder eingesetzt werden können.  Diese Components sind in `.razor`-Dateien gespeichert.
# UseEffect / Initializer
Wie bei React gibt es auch innerhalb von Blazor eine Funktion, die beim initialisieren eines Components aufgerufen wird. 
`protected override void OnInitialized()`
und
`public void Dispose()`
Es gibt ausserdem noch ein paar spezifischere Funktionen wie `OnAfterRender`und `OnParameterSet`.
## Beispiel
```JavaScript
import React, { useEffect } from 'react';  
  
function GreetingComponent() {  
  useEffect(() => {  
    console.log('Hello');  
  
    return () => {  
      console.log('Bye');  
    };  
  }, []);  
  
  return <div>Greeting Component</div>;  
}  
  
export default GreetingComponent;
```

```C#
# Muss implementiert werden, wenn die Dispose()-Methode verwendet werden soll.
@implements IDisposable  
  
@page "/greeting"  
  
<h3>Greeting Component</h3>  
  
@code {  
  
    protected override void OnInitialized()  
    {  
        Console.WriteLine("Hello");  
    }  
  
    public void Dispose()  
    {  
        Console.WriteLine("Bye");  
    }  
}
```
# Inputs nehmen
Wie in React muss man auch in Blazor eine Funktion aufrufen, wenn sich der Text in einem Eingabefeld ändert:
```C#
@rendermode InteractiveServer

<Input oninput="@onInputChanged"/>

@code {
	private string _inputValue = "";
	private void OnInputChanged(ChangeEventArgs eventArgs){
		_inputValue = eventArgs.Value.ToString();
	}
}
```
# Component -Parameter (useState)
Um einem Component einen Parameter zu geben, muss die entsprechende Variable im `@code`-Teil des Components mit dem Attribut `[Parameter]` versehen werden.

Ist der Parameter an eine Variable gebunden, wird er immer neu gesetzt, wenn sich diese verändert. So erspart man sich sen useState-Hook, welchen man in React bräuchte.

Der Component:
```c#
@rendermode InteractiveServer
<h1>Counter</h1>
<p role="status">Current count: @currentcount</p>
<button class="btn" @onclick="IncrementCount">Click me</button>

@code{
	private int currentCount = 0;
	
	[Parameter]
	public int IncrementAmount {get; set;} = 1;
	
	private void IncrementCount(){
		currentCount += IncrementAmount;
	}
}
```
Wird folgendermassen verwendet:
```c#
@page "/"

<h1>My Page</h1>
<Counter IncrementAmount="42"/>
```
# Values von Child zu Parent passen
Um den Parent-Component über ein Event zu informieren, sollte man ein `EventCallback` verwenden. Der Child-Component implementiert ein Event, welches mit dem Attribute `[Parameter]`versehen ist. 
Der Parent versieht diesen `EventCallback` mit einer Methode.
## Child
```c#
@rendermode InteractiveServer

<input onchange="@_onInputChanged"/>

@code{
	// This will get set by the parent
	[Parameter]
	public EventCallback<string> OnInputChanged { get; set; }

	// Input EventHandler gibt Parameter an EventCallback weiter
	private async Task _onInputChanged(ChangeEventArgs args){
		await OnInputChanged.InvokeAsync(args.Value.ToString())
	}
}
```
## Parent
```c#
<MyChildComponent OnInputChanged="s=>TextInputChanged(s)"/>

@code{
	protected async Task TextInputChanged(string s){
		Console.WriteLine("Text input changed!")
	}
}
```

[Quelle](https://www.pragimtech.com/blog/blazor/pass-data-from-child-to-parent-component-in-blazor/)
