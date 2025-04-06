```
reinterpret(reshape, T, A::AbstractArray{S}) -> B
```

Cambia la interpretación de tipo de `A` mientras consume o añade una "dimensión de canal".

Si `sizeof(T) = n*sizeof(S)` para `n>1`, la primera dimensión de `A` debe ser de tamaño `n` y `B` carece de la primera dimensión de `A`. Por el contrario, si `sizeof(S) = n*sizeof(T)` para `n>1`, `B` obtiene una nueva primera dimensión de tamaño `n`. La dimensionalidad no cambia si `sizeof(T) == sizeof(S)`.

!!! compat "Julia 1.6"
    Este método requiere al menos Julia 1.6.


# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> reinterpret(reshape, Complex{Int}, A)    # el resultado es un vector
2-element reinterpret(reshape, Complex{Int64}, ::Matrix{Int64}) with eltype Complex{Int64}:
 1 + 3im
 2 + 4im

julia> a = [(1,2,3), (4,5,6)]
2-element Vector{Tuple{Int64, Int64, Int64}}:
 (1, 2, 3)
 (4, 5, 6)

julia> reinterpret(reshape, Int, a)             # el resultado es una matriz
3×2 reinterpret(reshape, Int64, ::Vector{Tuple{Int64, Int64, Int64}}) with eltype Int64:
 1  4
 2  5
 3  6
```
