```
push!(collection, items...) -> collection
```

Inserta uno o más `items` en `collection`. Si `collection` es un contenedor ordenado, los elementos se insertan al final (en el orden dado).

# Ejemplos

```jldoctest
julia> push!([1, 2, 3], 4, 5, 6)
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

Si `collection` es ordenado, usa [`append!`](@ref) para agregar todos los elementos de otro contenedor a él. El resultado del ejemplo anterior es equivalente a `append!([1, 2, 3], [4, 5, 6])`. Para objetos `AbstractSet`, se puede usar [`union!`](@ref) en su lugar.

Consulta [`sizehint!`](@ref) para notas sobre el modelo de rendimiento.

Consulta también [`pushfirst!`](@ref).
