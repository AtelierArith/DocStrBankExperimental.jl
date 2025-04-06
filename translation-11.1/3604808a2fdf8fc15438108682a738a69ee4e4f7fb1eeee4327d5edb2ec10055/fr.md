```
pushfirst!(collection, items...) -> collection
```

Insère un ou plusieurs `items` au début de `collection`.

Cette fonction est appelée `unshift` dans de nombreux autres langages de programmation.

# Exemples

```jldoctest
julia> pushfirst!([1, 2, 3, 4], 5, 6)
6-element Vector{Int64}:
 5
 6
 1
 2
 3
 4
```
