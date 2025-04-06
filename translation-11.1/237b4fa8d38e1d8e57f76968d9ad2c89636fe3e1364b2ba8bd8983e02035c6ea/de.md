```
@sync
```

Warten Sie, bis alle lexikalisch eingeschlossenen Verwendungen von [`@async`](@ref), [`@spawn`](@ref Threads.@spawn), `Distributed.@spawnat` und `Distributed.@distributed` abgeschlossen sind. Alle Ausnahmen, die von den eingeschlossenen asynchronen Operationen ausgelöst werden, werden gesammelt und als [`CompositeException`](@ref) ausgelöst.

# Beispiele

```julia-repl
julia> Threads.nthreads()
4

julia> @sync begin
           Threads.@spawn println("Thread-id $(Threads.threadid()), task 1")
           Threads.@spawn println("Thread-id $(Threads.threadid()), task 2")
       end;
Thread-id 3, task 1
Thread-id 1, task 2
```
