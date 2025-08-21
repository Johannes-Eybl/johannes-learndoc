#ÜK
#frontend

# Lernziele

- Du verstehst, wie du auf Änderungen des States mittels dem *useEffect* Hook reagieren kannst
- Du verstehst den Lebenszyklus eines Components und wie du diesen mittels *useEffekt* nutzen kannst
- Du kansnt mit der fetch-Api Daten eines Servers darstellen

# Grundsätzliche Erklärung von *useEffect*

useEffect wird dazu verwendet, auf die Änderung eines States zu reagieren. Dazu wird dem useEffect eine Methode gegeben, die ausgelöst werden soll, sowie ein Array mit Variabeln, bei deren Änderung die Methode ausgelöst werden soll. Die Inhalte von diesem Array werden *Dependencies* genannt.

# Funktionen zu bestimmten Zeitpunkten ausführen

Man kann das *Dependency*-Array leer lassen, dann wird die Funktion nur einmal beim Laden des Components im DOM ausgeführt.

Wenn man als Rückgabewert eine Funktion verwendet (eine Funktion zurück gibt),  wird diese zurückgegebene Funktion erst ausgelöst, wenn der *Component* die DOM verlässt (*bevor* es die DOM verlässt). Das passiert auch, wenn ein *Component* gegeben ist. In diesem Fall wird die Rückgabewert-Funktion beim Ändern der Variabel ausglöst. (Es wird zuerst die Rückgabewert-Funktion und danach die eigentliche Funktion ausgelöst)

Das ist vergleichbar mit “Constructor” und “Destructor” *(kein guter Vergleich -Yves)*.