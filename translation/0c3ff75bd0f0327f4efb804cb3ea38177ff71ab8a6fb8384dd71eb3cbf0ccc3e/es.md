```
findnext(A, i)
```

Encuentra el siguiente índice después o incluyendo `i` de un elemento `true` de `A`, o `nothing` si no se encuentra.

Los índices son del mismo tipo que los devueltos por [`keys(A)`](@ref) y [`pairs(A)`](@ref).

# Ejemplos

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findnext(A, 1)
3

julia> findnext(A, 4) # devuelve nothing, pero no se imprime en el REPL

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findnext(A, CartesianIndex(1, 1))
CartesianIndex(2, 1)
```
