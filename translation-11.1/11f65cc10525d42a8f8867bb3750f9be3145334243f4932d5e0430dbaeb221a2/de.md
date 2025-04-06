```
Event([autoreset=false])
```

Erstellen Sie eine level-triggered Ereignisquelle. Aufgaben, die [`wait`](@ref) auf einem `Event` aufrufen, werden ausgesetzt und in eine Warteschlange gestellt, bis [`notify`](@ref) auf dem `Event` aufgerufen wird. Nachdem `notify` aufgerufen wurde, bleibt das `Event` im signalisierenden Zustand, und Aufgaben werden nicht mehr blockiert, wenn sie darauf warten, bis `reset` aufgerufen wird.

Wenn `autoreset` wahr ist, wird höchstens eine Aufgabe aus `wait` für jeden Aufruf von `notify` freigegeben.

Dies bietet eine Erwerbs- und Freigabereihenfolge im Speicher für notify/wait.

!!! compat "Julia 1.1"
    Diese Funktionalität erfordert mindestens Julia 1.1.


!!! compat "Julia 1.8"
    Die `autoreset`-Funktionalität und die Garantie der Speicherreihenfolge erfordern mindestens Julia 1.8.

