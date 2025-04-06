```
put!(c::Channel, v)
```

Fügt ein Element `v` zum Kanal `c` hinzu. Blockiert, wenn der Kanal voll ist.

Für unpufferte Kanäle blockiert es, bis ein [`take!`](@ref) von einer anderen Aufgabe ausgeführt wird.

!!! compat "Julia 1.1"
    `v` wird jetzt in den Typ des Kanals mit [`convert`](@ref) umgewandelt, wenn `put!` aufgerufen wird.

