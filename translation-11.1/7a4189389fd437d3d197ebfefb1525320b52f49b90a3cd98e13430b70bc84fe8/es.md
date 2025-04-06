```
findlast(predicate::Function, A)
```

Devuelve el índice o clave del último elemento de `A` para el cual `predicate` devuelve `true`. Devuelve `nothing` si no hay tal elemento.

Los índices o claves son del mismo tipo que los devueltos por [`keys(A)`](@ref) y [`pairs(A)`](@ref).

# Ejemplos

```jldoctest
julia> A = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> findlast(isodd, A)
3

julia> findlast(x -> x > 5, A) # devuelve nothing, pero no se imprime en el REPL

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> findlast(isodd, A)
CartesianIndex(2, 1)
```
