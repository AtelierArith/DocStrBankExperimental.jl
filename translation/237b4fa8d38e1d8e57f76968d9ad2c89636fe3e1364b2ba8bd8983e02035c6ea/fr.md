```
@sync
```

Attendez que toutes les utilisations lexicalement enfermées de [`@async`](@ref), [`@spawn`](@ref Threads.@spawn), `Distributed.@spawnat` et `Distributed.@distributed` soient terminées. Toutes les exceptions levées par les opérations asynchrones enfermées sont collectées et levées sous la forme d'une [`CompositeException`](@ref).

# Exemples

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
