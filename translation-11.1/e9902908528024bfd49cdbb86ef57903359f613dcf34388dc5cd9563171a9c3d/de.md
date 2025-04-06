```
isabspath(path::AbstractString) -> Bool
```

Bestimmen Sie, ob ein Pfad absolut ist (am Wurzelverzeichnis beginnt).

# Beispiele

```jldoctest
julia> isabspath("/home")
true

julia> isabspath("home")
false
```
