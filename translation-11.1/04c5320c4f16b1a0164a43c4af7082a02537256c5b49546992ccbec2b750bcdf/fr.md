```
dropwhile(pred, iter)
```

Un itérateur qui supprime les éléments de `iter` tant que le prédicat `pred` est vrai, puis retourne chaque élément.

!!! compat "Julia 1.4"
    Cette fonction nécessite au moins Julia 1.4.


# Exemples

```jldoctest
julia> s = collect(1:5)
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> collect(Iterators.dropwhile(<(3),s))
3-element Vector{Int64}:
 3
 4
 5
```
