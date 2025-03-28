```
Condition()
```

Erstellen Sie eine kantengetriggerte Ereignisquelle, auf die Aufgaben warten können. Aufgaben, die [`wait`](@ref) auf einer `Condition` aufrufen, werden ausgesetzt und in eine Warteschlange gestellt. Aufgaben werden geweckt, wenn später [`notify`](@ref) auf der `Condition` aufgerufen wird. Das Warten auf eine Bedingung kann einen Wert zurückgeben oder einen Fehler auslösen, wenn die optionalen Argumente von [`notify`](@ref) verwendet werden. Kantentrigger bedeutet, dass nur Aufgaben, die zum Zeitpunkt des Aufrufs von [`notify`](@ref) warten, geweckt werden können. Für levelgetriggerte Benachrichtigungen müssen Sie zusätzlichen Zustand beibehalten, um zu verfolgen, ob eine Benachrichtigung stattgefunden hat. Die Typen [`Channel`](@ref) und [`Threads.Event`](@ref) tun dies und können für levelgetriggerte Ereignisse verwendet werden.

Dieses Objekt ist NICHT threadsicher. Siehe [`Threads.Condition`](@ref) für eine threadsichere Version.
