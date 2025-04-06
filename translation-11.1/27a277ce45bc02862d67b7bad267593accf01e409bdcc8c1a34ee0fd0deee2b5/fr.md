```
splitpath(path::AbstractString) -> Vector{String}
```

Divise un chemin de fichier en tous ses composants de chemin. C'est l'opposé de `joinpath`. Renvoie un tableau de sous-chaînes, une pour chaque répertoire ou fichier dans le chemin, y compris le répertoire racine s'il est présent.

!!! compat "Julia 1.1"
    Cette fonction nécessite au moins Julia 1.1.


# Exemples

```jldoctest
julia> splitpath("/home/myuser/example.jl")
4-element Vector{String}:
 "/"
 "home"
 "myuser"
 "example.jl"
```
