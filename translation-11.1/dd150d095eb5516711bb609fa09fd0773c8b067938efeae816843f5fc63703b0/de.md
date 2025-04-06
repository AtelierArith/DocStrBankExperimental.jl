```
Threads.@spawn [:default|:interactive] expr
```

Erstellt eine [`Task`](@ref) und [`schedule`](@ref) sie zur Ausführung auf einem verfügbaren Thread im angegebenen Threadpool (`:default`, wenn nicht angegeben). Die Aufgabe wird einem Thread zugewiesen, sobald einer verfügbar wird. Um auf den Abschluss der Aufgabe zu warten, rufen Sie [`wait`](@ref) auf dem Ergebnis dieses Makros auf oder rufen Sie [`fetch`](@ref) auf, um zu warten und dann den Rückgabewert zu erhalten.

Werte können über `$` in `@spawn` interpoliert werden, was den Wert direkt in die konstruierte zugrunde liegende Closure kopiert. Dies ermöglicht es Ihnen, den *Wert* einer Variablen einzufügen und den asynchronen Code von Änderungen am Wert der Variablen in der aktuellen Aufgabe zu isolieren.

!!! note
    Der Thread, auf dem die Aufgabe ausgeführt wird, kann sich ändern, wenn die Aufgabe yieldet, daher sollte `threadid()` nicht als konstant für eine Aufgabe betrachtet werden. Siehe [`Task Migration`](@ref man-task-migration) und das umfassendere [Multi-Threading](@ref man-multithreading) Handbuch für weitere wichtige Hinweise. Siehe auch das Kapitel über [Threadpools](@ref man-threadpools).


!!! compat "Julia 1.3"
    Dieses Makro ist seit Julia 1.3 verfügbar.


!!! compat "Julia 1.4"
    Die Interpolation von Werten über `$` ist seit Julia 1.4 verfügbar.


!!! compat "Julia 1.9"
    Ein Threadpool kann seit Julia 1.9 angegeben werden.


# Beispiele

```julia-repl
julia> t() = println("Hello from ", Threads.threadid());

julia> tasks = fetch.([Threads.@spawn t() for i in 1:4]);
Hello from 1
Hello from 1
Hello from 3
Hello from 4
```
