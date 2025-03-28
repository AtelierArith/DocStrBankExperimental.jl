```
@atomicswap a.b.x = new
@atomicswap :sequentially_consistent a.b.x = new
```

Stocke `new` dans `a.b.x` et renvoie l'ancienne valeur de `a.b.x`.

Cette opération se traduit par un appel à `swapproperty!(a.b, :x, new)`.

Voir la section [Per-field atomics](@ref man-atomics) dans le manuel pour plus de détails.

# Exemples

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicswap a.x = 2+2 # remplacer le champ x de a par 4, avec cohérence séquentielle
1

julia> @atomic a.x # récupérer le champ x de a, avec cohérence séquentielle
4
```

!!! compat "Julia 1.7"
    Cette fonctionnalité nécessite au moins Julia 1.7.

