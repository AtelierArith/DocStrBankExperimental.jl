```
@atomiconce a.b.x = valeur
@atomiconce :sequentially_consistent a.b.x = valeur
@atomiconce :sequentially_consistent :monotonic a.b.x = valeur

Effectuez l'assignation conditionnelle de valeur de manière atomique si elle n'était pas précédemment définie, en retournant la valeur `success::Bool`. Où `success` indique si l'assignation a été complétée.

Cette opération se traduit par un appel à `setpropertyonce!(a.b, :x, valeur)`.

Voir la section [Per-field atomics](@ref man-atomics) dans le manuel pour plus de détails.

# Exemples

```

jldoctest julia> mutable struct AtomicOnce            @atomic x            AtomicOnce() = new()        end

julia> a = AtomicOnce() AtomicOnce(#undef)

julia> @atomiconce a.x = 1 # définir le champ x de a à 1, si non défini, avec cohérence séquentielle true

julia> @atomic a.x # récupérer le champ x de a, avec cohérence séquentielle 1

julia> @atomiconce a.x = 1 # définir le champ x de a à 1, si non défini, avec cohérence séquentielle false

```

!!! compat "Julia 1.11"
    Cette fonctionnalité nécessite au moins Julia 1.11.
```
