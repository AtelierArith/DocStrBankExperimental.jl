```
rest(iter, state)
```

Un itérateur qui produit les mêmes éléments que `iter`, mais en commençant à l'état donné.

Voir aussi : [`Iterators.drop`](@ref), [`Iterators.peel`](@ref), [`Base.rest`](@ref).

# Exemples

```jldoctest
julia> collect(Iterators.rest([1,2,3,4], 2))
3-element Vector{Int64}:
 2
 3
 4
```
