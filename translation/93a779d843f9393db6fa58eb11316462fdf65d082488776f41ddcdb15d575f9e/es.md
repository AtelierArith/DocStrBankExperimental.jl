```
lastindex(collection) -> Integer
lastindex(collection, d) -> Integer
```

Devuelve el último índice de `collection`. Si se proporciona `d`, devuelve el último índice de `collection` a lo largo de la dimensión `d`.

Las sintaxis `A[end]` y `A[end, end]` se traducen a `A[lastindex(A)]` y `A[lastindex(A, 1), lastindex(A, 2)]`, respectivamente.

Véase también: [`axes`](@ref), [`firstindex`](@ref), [`eachindex`](@ref), [`prevind`](@ref).

# Ejemplos

```jldoctest
julia> lastindex([1,2,4])
3

julia> lastindex(rand(3,4,5), 2)
4
```
