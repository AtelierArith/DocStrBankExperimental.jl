```
@sync
```

Espera hasta que se completen todos los usos encerrados léxicamente de [`@async`](@ref), [`@spawn`](@ref Threads.@spawn), `Distributed.@spawnat` y `Distributed.@distributed`. Todas las excepciones lanzadas por las operaciones asíncronas encerradas se recopilan y se lanzan como una [`CompositeException`](@ref).

# Ejemplos

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
