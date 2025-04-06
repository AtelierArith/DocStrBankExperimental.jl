```
basename(path::AbstractString) -> String
```

Obtenez la partie nom de fichier d'un chemin.

!!! note
    Cette fonction diffère légèrement du programme Unix `basename`, où les barres obliques finales sont ignorées, c'est-à-dire que `$ basename /foo/bar/` renvoie `bar`, tandis que `basename` en Julia renvoie une chaîne vide `""`.


# Exemples

```jldoctest
julia> basename("/home/myuser/example.jl")
"example.jl"

julia> basename("/home/myuser/")
""
```

Voir aussi [`dirname`](@ref).
