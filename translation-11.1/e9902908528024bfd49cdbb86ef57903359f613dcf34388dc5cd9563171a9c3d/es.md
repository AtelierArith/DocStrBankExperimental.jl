```
isabspath(path::AbstractString) -> Bool
```

Determina si una ruta es absoluta (comienza en el directorio raíz).

# Ejemplos

```jldoctest
julia> isabspath("/home")
true

julia> isabspath("home")
false
```
