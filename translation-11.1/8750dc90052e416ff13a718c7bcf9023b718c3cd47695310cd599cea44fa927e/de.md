```
wait(c::Channel)
```

Blockiert, bis der `Channel` [`isready`](@ref) ist.

```jldoctest
julia> c = Channel(1);

julia> isready(c)
false

julia> task = Task(() -> wait(c));

julia> schedule(task);

julia> istaskdone(task)  # Aufgabe ist blockiert, weil der Kanal nicht bereit ist
false

julia> put!(c, 1);

julia> istaskdone(task)  # Aufgabe ist jetzt nicht mehr blockiert
true
```
