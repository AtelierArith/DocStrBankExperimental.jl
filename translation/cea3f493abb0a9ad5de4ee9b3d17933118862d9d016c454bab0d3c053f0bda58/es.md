```
findprev(predicate::Function, A, i)
```

Encuentra el índice anterior antes o incluyendo `i` de un elemento de `A` para el cual `predicate` devuelve `true`, o `nothing` si no se encuentra. Esto funciona para Arrays, Cadenas y la mayoría de otras colecciones que soportan [`getindex`](@ref), [`keys(A)`](@ref), y [`nextind`](@ref).

Los índices son del mismo tipo que los devueltos por [`keys(A)`](@ref) y [`pairs(A)`](@ref).

# Ejemplos

```jldoctest
julia> A = [4, 6, 1, 2]
4-element Vector{Int64}:
 4
 6
 1
 2

julia> findprev(isodd, A, 1) # devuelve nothing, pero no se imprime en el REPL

julia> findprev(isodd, A, 3)
3

julia> A = [4 6; 1 2]
2×2 Matrix{Int64}:
 4  6
 1  2

julia> findprev(isodd, A, CartesianIndex(1, 2))
CartesianIndex(2, 1)

julia> findprev(isspace, "a b c", 3)
2
```
