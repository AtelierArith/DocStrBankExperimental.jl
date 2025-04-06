```
firstindex(collection) -> Integer
firstindex(collection, d) -> Integer
```

Devuelve el primer índice de `collection`. Si se proporciona `d`, devuelve el primer índice de `collection` a lo largo de la dimensión `d`.

Las sintaxis `A[begin]` y `A[1, begin]` se traducen a `A[firstindex(A)]` y `A[1, firstindex(A, 2)]`, respectivamente.

Véase también: [`first`](@ref), [`axes`](@ref), [`lastindex`](@ref), [`nextind`](@ref).

# Ejemplos

```jldoctest
julia> firstindex([1,2,4])
1

julia> firstindex(rand(3,4,5), 2)
1
```
