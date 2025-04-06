```
isdir(path) -> Bool
```

Devuelve `true` si `path` es un directorio, `false` en caso contrario.

# Ejemplos

```jldoctest
julia> isdir(homedir())
true

julia> isdir("not/a/directory")
false
```

Consulta también [`isfile`](@ref) y [`ispath`](@ref). ```
