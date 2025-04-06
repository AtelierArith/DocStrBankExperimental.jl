```
dirname(path::AbstractString) -> String
```

Obtenez la partie répertoire d'un chemin. Les caractères de fin ('/' ou '\') dans le chemin sont comptés comme faisant partie du chemin.

# Exemples

```jldoctest
julia> dirname("/home/myuser")
"/home"

julia> dirname("/home/myuser/")
"/home/myuser"
```

Voir aussi [`basename`](@ref).
