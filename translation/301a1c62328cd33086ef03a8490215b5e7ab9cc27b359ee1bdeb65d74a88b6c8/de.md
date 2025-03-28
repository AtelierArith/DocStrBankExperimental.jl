```
istaskfailed(t::Task) -> Bool
```

Bestimmen Sie, ob eine Aufgabe aufgrund einer Ausnahme beendet wurde.

# Beispiele

```jldoctest
julia> a4() = error("Aufgabe fehlgeschlagen");

julia> b = Task(a4);

julia> istaskfailed(b)
false

julia> schedule(b);

julia> yield();

julia> istaskfailed(b)
true
```

!!! compat "Julia 1.3"
    Diese Funktion erfordert mindestens Julia 1.3.

