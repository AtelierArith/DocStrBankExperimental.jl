```
firstindex(collection) -> Integer
firstindex(collection, d) -> Integer
```

Retourne le premier index de `collection`. Si `d` est donné, retourne le premier index de `collection` le long de la dimension `d`.

Les syntaxes `A[begin]` et `A[1, begin]` se traduisent par `A[firstindex(A)]` et `A[1, firstindex(A, 2)]`, respectivement.

Voir aussi : [`first`](@ref), [`axes`](@ref), [`lastindex`](@ref), [`nextind`](@ref).

# Exemples

```jldoctest
julia> firstindex([1,2,4])
1

julia> firstindex(rand(3,4,5), 2)
1
```
