```
last(coll)
```

Obtenez le dernier élément d'une collection ordonnée, si cela peut être calculé en O(1) temps. Cela est accompli en appelant [`lastindex`](@ref) pour obtenir le dernier index. Retournez le point final d'un [`AbstractRange`](@ref) même s'il est vide.

Voir aussi [`first`](@ref), [`endswith`](@ref).

# Exemples

```jldoctest
julia> last(1:2:10)
9

julia> last([1; 2; 3; 4])
4
```
