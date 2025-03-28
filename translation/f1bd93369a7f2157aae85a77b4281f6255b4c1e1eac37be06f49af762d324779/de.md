```
istaskstarted(t::Task) -> Bool
```

Bestimmen Sie, ob eine Aufgabe mit der Ausführung begonnen hat.

# Beispiele

```jldoctest
julia> a3() = sum(i for i in 1:1000);

julia> b = Task(a3);

julia> istaskstarted(b)
false
```
