```
wait(c::Channel)
```

Bloque jusqu'à ce que le `Channel` [`isready`](@ref).

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> task = Task(() -> wait(c));

julia> schedule(task);

julia> istaskdone(task)  # la tâche est bloquée car le canal n'est pas prêt
false

julia> put!(c, 1);

julia> istaskdone(task)  # la tâche n'est plus bloquée
true
```
