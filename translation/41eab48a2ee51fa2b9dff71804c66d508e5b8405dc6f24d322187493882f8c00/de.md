```
Timer(delay; interval = 0)
```

Erstellen Sie einen Timer, der Aufgaben weckt, die auf ihn warten (indem [`wait`](@ref) auf dem Timer-Objekt aufgerufen wird).

Wartende Aufgaben werden nach einer anfänglichen Verzögerung von mindestens `delay` Sekunden geweckt und wiederholt, nachdem erneut mindestens `interval` Sekunden vergangen sind. Wenn `interval` gleich `0` ist, wird der Timer nur einmal ausgelöst. Wenn der Timer geschlossen wird (durch [`close`](@ref)), werden wartende Aufgaben mit einem Fehler geweckt. Verwenden Sie [`isopen`](@ref), um zu überprüfen, ob ein Timer noch aktiv ist.

!!! note
    `interval` unterliegt der Ansammlung von Zeitabweichungen. Wenn Sie präzise Ereignisse zu einem bestimmten absoluten Zeitpunkt benötigen, erstellen Sie bei jedem Ablauf einen neuen Timer mit der Differenz zur nächsten Zeit, die berechnet wird.


!!! note
    Ein `Timer` erfordert Ertragspunkte, um seinen Zustand zu aktualisieren. Zum Beispiel kann `isopen(t::Timer)` nicht verwendet werden, um eine nicht-ertragende While-Schleife zu beenden.

