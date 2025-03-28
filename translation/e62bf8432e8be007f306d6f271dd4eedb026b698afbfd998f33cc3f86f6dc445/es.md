```
findfirst(predicate::Function, A)
```

Devuelve el índice o clave del primer elemento de `A` para el cual `predicate` devuelve `true`. Devuelve `nothing` si no hay tal elemento.

Los índices o claves son del mismo tipo que los devueltos por [`keys(A)`](@ref) y [`pairs(A)`](@ref).

# Ejemplos

```jldoctest
julia> A = [1, 4, 2, 2]
4-element Vector{Int64}:
 1
 4
 2
 2

julia> findfirst(iseven, A)
2

julia> findfirst(x -> x>10, A) # devuelve nothing, pero no se imprime en el REPL

julia> findfirst(isequal(4), A)
2

julia> A = [1 4; 2 2]
2×2 Matrix{Int64}:
 1  4
 2  2

julia> findfirst(iseven, A)
CartesianIndex(2, 1)
```
