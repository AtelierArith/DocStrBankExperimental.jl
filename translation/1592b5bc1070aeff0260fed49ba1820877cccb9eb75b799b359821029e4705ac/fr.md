```
@atomicreplace a.b.x attendu => désiré
@atomicreplace :sequentially_consistent a.b.x attendu => désiré
@atomicreplace :sequentially_consistent :monotonic a.b.x attendu => désiré
```

Effectuez le remplacement conditionnel exprimé par la paire de manière atomique, en retournant les valeurs `(ancien, succès::Bool)`. Où `succès` indique si le remplacement a été effectué.

Cette opération se traduit par un appel à `replaceproperty!(a.b, :x, attendu, désiré)`.

Voir la section [Per-field atomics](@ref man-atomics) dans le manuel pour plus de détails.

# Exemples

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomicreplace a.x 1 => 2 # remplacer le champ x de a par 2 s'il était 1, avec cohérence séquentielle
(ancien = 1, succès = true)

julia> @atomic a.x # récupérer le champ x de a, avec cohérence séquentielle
2

julia> @atomicreplace a.x 1 => 2 # remplacer le champ x de a par 2 s'il était 1, avec cohérence séquentielle
(ancien = 2, succès = false)

julia> xchg = 2 => 0; # remplacer le champ x de a par 0 s'il était 2, avec cohérence séquentielle

julia> @atomicreplace a.x xchg
(ancien = 2, succès = true)

julia> @atomic a.x # récupérer le champ x de a, avec cohérence séquentielle
0
```

!!! compat "Julia 1.7"
    Cette fonctionnalité nécessite au moins Julia 1.7.

