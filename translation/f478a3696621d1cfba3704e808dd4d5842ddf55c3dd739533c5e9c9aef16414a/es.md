```
getindex(A, inds...)
```

Devuelve un subconjunto del arreglo `A` según lo seleccionado por los índices `inds`.

Cada índice puede ser de cualquier [tipo de índice soportado](@ref man-supported-index-types), como un [`Integer`](@ref), [`CartesianIndex`](@ref), [rango](@ref Base.AbstractRange), o [arreglo](@ref man-multi-dim-arrays) de índices soportados. Un [:](@ref Base.Colon) puede ser utilizado para seleccionar todos los elementos a lo largo de una dimensión específica, y un arreglo booleano (por ejemplo, un `Array{Bool}` o un [`BitArray`](@ref)) puede ser utilizado para filtrar elementos donde el índice correspondiente es `true`.

Cuando `inds` selecciona múltiples elementos, esta función devuelve un arreglo recién asignado. Para indexar múltiples elementos sin hacer una copia, utiliza [`view`](@ref) en su lugar.

Consulta la sección del manual sobre [indexación de arreglos](@ref man-array-indexing) para más detalles.

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> getindex(A, 1)
1

julia> getindex(A, [2, 1])
2-element Vector{Int64}:
 3
 1

julia> getindex(A, 2:4)
3-element Vector{Int64}:
 3
 2
 4

julia> getindex(A, 2, 1)
3

julia> getindex(A, CartesianIndex(2, 1))
3

julia> getindex(A, :, 2)
2-element Vector{Int64}:
 2
 4

julia> getindex(A, 2, :)
2-element Vector{Int64}:
 3
 4

julia> getindex(A, A .> 2)
2-element Vector{Int64}:
 3
 4
```
