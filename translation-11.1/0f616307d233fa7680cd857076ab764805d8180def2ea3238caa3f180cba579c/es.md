```
max(x, y, ...)
```

Devuelve el máximo de los argumentos, con respecto a [`isless`](@ref). Si alguno de los argumentos es [`missing`](@ref), devuelve `missing`. Consulta también la función [`maximum`](@ref) para obtener el elemento máximo de una colección.

# Ejemplos

```jldoctest
julia> max(2, 5, 1)
5

julia> max(5, missing, 6)
missing
```
