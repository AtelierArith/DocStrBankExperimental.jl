```
lastindex(collection) -> Integer
lastindex(collection, d) -> Integer
```

Retourne le dernier index de `collection`. Si `d` est donné, retourne le dernier index de `collection` le long de la dimension `d`.

Les syntaxes `A[end]` et `A[end, end]` se traduisent par `A[lastindex(A)]` et `A[lastindex(A, 1), lastindex(A, 2)]`, respectivement.

Voir aussi : [`axes`](@ref), [`firstindex`](@ref), [`eachindex`](@ref), [`prevind`](@ref).

# Exemples

```jldoctest
julia> lastindex([1,2,4])
3

julia> lastindex(rand(3,4,5), 2)
4
```
