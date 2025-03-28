```
findprev(A, i)
```

Encuentra el índice anterior antes o incluyendo `i` de un elemento `true` de `A`, o `nothing` si no se encuentra.

Los índices son del mismo tipo que los devueltos por [`keys(A)`](@ref) y [`pairs(A)`](@ref).

Véase también: [`findnext`](@ref), [`findfirst`](@ref), [`findall`](@ref).

# Ejemplos

```jldoctest
julia> A = [false, false, true, true]
4-element Vector{Bool}:
 0
 0
 1
 1

julia> findprev(A, 3)
3

julia> findprev(A, 1) # devuelve nothing, pero no se imprime en el REPL

julia> A = [false false; true true]
2×2 Matrix{Bool}:
 0  0
 1  1

julia> findprev(A, CartesianIndex(2, 1))
CartesianIndex(2, 1)
```
