```
isabspath(path::AbstractString) -> Bool
```

Déterminez si un chemin est absolu (commence à partir du répertoire racine).

# Exemples

```jldoctest
julia> isabspath("/home")
true

julia> isabspath("home")
false
```
