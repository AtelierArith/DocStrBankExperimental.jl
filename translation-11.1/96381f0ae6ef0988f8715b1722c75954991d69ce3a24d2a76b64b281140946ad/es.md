```
dirname(path::AbstractString) -> String
```

Obtiene la parte del directorio de una ruta. Los caracteres finales ('/' o '\') en la ruta se cuentan como parte de la ruta.

# Ejemplos

```jldoctest
julia> dirname("/home/myuser")
"/home"

julia> dirname("/home/myuser/")
"/home/myuser"
```

Ver también [`basename`](@ref).
