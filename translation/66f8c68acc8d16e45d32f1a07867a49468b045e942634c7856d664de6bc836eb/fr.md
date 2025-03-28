```
UnitRange{T<:Réel}
```

Un intervalle paramétré par un `début` et un `fin` de type `T`, rempli d'éléments espacés de `1` depuis `début` jusqu'à ce que `fin` soit dépassé. La syntaxe `a:b` avec `a` et `b` étant tous deux des `Entiers` crée un `UnitRange`.

# Exemples

```jldoctest
julia> collect(UnitRange(2.3, 5.2))
3-element Vector{Float64}:
 2.3
 3.3
 4.3

julia> typeof(1:10)
UnitRange{Int64}
```
