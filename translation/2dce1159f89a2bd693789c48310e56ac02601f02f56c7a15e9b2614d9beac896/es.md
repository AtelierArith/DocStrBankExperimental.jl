```
isdirpath(path::AbstractString) -> Bool
```

Determina si una ruta se refiere a un directorio (por ejemplo, termina con un separador de ruta).

# Ejemplos

```jldoctest
julia> isdirpath("/home")
false

julia> isdirpath("/home/")
true
```
