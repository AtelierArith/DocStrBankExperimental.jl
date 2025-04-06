```
isfile(path) -> Bool
```

Devuelve `true` si `path` es un archivo regular, `false` en caso contrario.

# Ejemplos

```jldoctest
julia> isfile(homedir())
false

julia> filename = "test_file.txt";

julia> write(filename, "¡Hola mundo!");

julia> isfile(filename)
true

julia> rm(filename);

julia> isfile(filename)
false
```

Consulta también [`isdir`](@ref) y [`ispath`](@ref).
