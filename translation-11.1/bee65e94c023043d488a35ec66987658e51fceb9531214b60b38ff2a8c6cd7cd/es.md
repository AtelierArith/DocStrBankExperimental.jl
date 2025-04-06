```
stride1(A) -> Int
```

Devuelve la distancia entre elementos sucesivos de la matriz en la dimensión 1 en unidades de tamaño de elemento.

# Ejemplos

```jldoctest
julia> A = [1,2,3,4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> LinearAlgebra.stride1(A)
1

julia> B = view(A, 2:2:4)
2-element view(::Vector{Int64}, 2:2:4) with eltype Int64:
 2
 4

julia> LinearAlgebra.stride1(B)
2
```
