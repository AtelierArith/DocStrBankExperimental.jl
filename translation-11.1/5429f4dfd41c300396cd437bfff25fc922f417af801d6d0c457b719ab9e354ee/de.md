```
WeakRef(x)
```

`w = WeakRef(x)` erstellt eine [schwache Referenz](https://en.wikipedia.org/wiki/Weak_reference) auf den Julia-Wert `x`: obwohl `w` eine Referenz auf `x` enthält, verhindert es nicht, dass `x` vom Garbage Collector gesammelt wird. `w.value` ist entweder `x` (wenn `x` noch nicht garbage-collected wurde) oder `nothing` (wenn `x` garbage-collected wurde).

```jldoctest
julia> x = "a string"
"a string"

julia> w = WeakRef(x)
WeakRef("a string")

julia> GC.gc()

julia> w           # eine Referenz wird über `x` aufrechterhalten
WeakRef("a string")

julia> x = nothing # Referenz löschen

julia> GC.gc()

julia> w
WeakRef(nothing)
```
