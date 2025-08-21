#angular #JavaScript #frontend 
Ein Observable ist ein Stream von Events oder Daten.
*Subscribing* triggert den observable-Stream. Ohne einen Observer wird der Stream nicht damit anfangen, Werte auszugeben. Wie bei einer Zeitung bekommt man die Daten nur, wenn man subscribed ist.

Observables werden am häufigsten bei [[HTTP-Requests]] verwendet.
# Observer-Functions
Jeder Observer hat drei Methoden:
- 'next' -> Verarbeitet den Empfang von neuen Daten aus dem Observable
- 'error' -> Verarbeitet Fehler, die auftreten
- 'complete' -> Verarbeitet den Abschluss bzw das Beenden eines Observers
# destroyRef
Wenn eine Subscription erstellt wird, dann muss diese auch wieder beendet werden. Denn praktisch ist eine Subscription eine Verbindung zwischen einem Component und einem Daten-Stream. Die Verbindung an sich weis nicht, ob der Component die Daten annehmen kann oder ob er zerstört ist. 

Wenn eine Subscription nach der Zerstörung eines Components weiter läuft, kann das zu unerwarteten Side Effects führen (Code läuft weiter obwohl der Component weg ist)!

Mit 'destroyRef' kann man sich beim [[Component Lifecycle]] einhängen, ohne die 'onDestroy'-Methode implementieren zu müssen.
```TypeScript
ngOnInit(){  
  const subscription = this.activatedRoute.paramMap.subscribe({  
    next: (paramMap) => {  
      this.userName = this.usersService.users.find(  
        (u) => u.id === paramMap.get('userId')  
      )?.name || '';  
    }  
  });  
  
  this.destroyRef.onDestroy(() => subscription.unsubscribe());  
}
```
In diesem Beispiel wird bei der Initialisierung des Components eine Subscription bei der 'activatedRoute' registriert. 
Innerhalb der Initialisierungs-Methode wird ebenfalls deklariert, dass die Subscription beim Zerstören des Components beendet werden soll. 
So muss die 'subscription'-Variable nicht ausserhalb der Initialisierungsmethode deklariert werden!
