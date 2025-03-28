```
findnext(predicate::Function, A, i)
```

Encuentra el siguiente índice después o incluyendo `i` de un elemento de `A` para el cual `predicate` devuelve `true`, o `nothing` si no se encuentra. Esto funciona para Arrays, Cadenas, y la mayoría de otras colecciones que soportan [`getindex`](@ref), [`keys(A)`](@ref), y [`nextind`](@ref).

Los índices son del mismo tipo que los devueltos por [`keys(A)`](@ref) y [`pairs(A)`](@ref).

# Ejemplos

```jldoctest
julia> A = [1, 4, 2, 2];

julia> findnext(isodd, A, 1)
1

julia> findnext(isodd, A, 2) # devuelve nothing, pero no se imprime en el REPL

julia> A = [1 4; 2 2];

julia> findnext(isodd, A, CartesianIndex(1, 1))
CartesianIndex(1, 1)

julia> findnext(isspace, "a b c", 3)
4
```
