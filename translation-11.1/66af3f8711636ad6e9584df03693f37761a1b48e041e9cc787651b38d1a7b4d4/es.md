```
min(x, y, ...)
```

Devuelve el mínimo de los argumentos, con respecto a [`isless`](@ref). Si alguno de los argumentos es [`missing`](@ref), devuelve `missing`. Consulta también la función [`minimum`](@ref) para obtener el elemento mínimo de una colección.

# Ejemplos

```jldoctest
julia> min(2, 5, 1)
1

julia> min(4, missing, 6)
missing
```
