```
isdirpath(path::AbstractString) -> Bool
```

Déterminez si un chemin fait référence à un répertoire (par exemple, se termine par un séparateur de chemin).

# Exemples

```jldoctest
julia> isdirpath("/home")
false

julia> isdirpath("/home/")
true
```
