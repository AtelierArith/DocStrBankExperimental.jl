```
wait(c::Channel)
```

Bloquea hasta que el `Channel` [`isready`](@ref).

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> task = Task(() -> wait(c));

julia> schedule(task);

julia> istaskdone(task)  # la tarea está bloqueada porque el canal no está listo
false

julia> put!(c, 1);

julia> istaskdone(task)  # la tarea ahora está desbloqueada
true
```
