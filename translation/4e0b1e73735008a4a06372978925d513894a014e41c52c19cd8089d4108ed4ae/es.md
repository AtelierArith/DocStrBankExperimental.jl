```
append!(collection, collections...) -> collection.
```

Para un contenedor ordenado `collection`, agrega los elementos de cada `collections` al final de él.

!!! compat "Julia 1.6"
    Especificar múltiples colecciones para ser añadidas requiere al menos Julia 1.6.


# Ejemplos

```jldoctest
julia> append!([1], [2, 3])
3-element Vector{Int64}:
 1
 2
 3

julia> append!([1, 2, 3], [4, 5], [6])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

Usa [`push!`](@ref) para agregar elementos individuales a `collection` que no estén ya en otra colección. El resultado del ejemplo anterior es equivalente a `push!([1, 2, 3], 4, 5, 6)`.

Consulta [`sizehint!`](@ref) para notas sobre el modelo de rendimiento.

Consulta también [`vcat`](@ref) para vectores, [`union!`](@ref) para conjuntos, y [`prepend!`](@ref) y [`pushfirst!`](@ref) para el orden opuesto.
