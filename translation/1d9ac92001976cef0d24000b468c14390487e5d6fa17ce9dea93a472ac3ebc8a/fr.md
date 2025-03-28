```
@atomic var
@atomic order ex
```

Marquez `var` ou `ex` comme étant exécuté de manière atomique, si `ex` est une expression supportée. Si aucun `order` n'est spécifié, il par défaut à :sequentially_consistent.

```
@atomic a.b.x = new
@atomic a.b.x += addend
@atomic :release a.b.x = new
@atomic :acquire_release a.b.x += addend
```

Effectuez l'opération de stockage exprimée à droite de manière atomique et renvoyez la nouvelle valeur.

Avec `=`, cette opération se traduit par un appel à `setproperty!(a.b, :x, new)`. Avec n'importe quel opérateur également, cette opération se traduit par un appel à `modifyproperty!(a.b, :x, +, addend)[2]`.

```
@atomic a.b.x max arg2
@atomic a.b.x + arg2
@atomic max(a.b.x, arg2)
@atomic :acquire_release max(a.b.x, arg2)
@atomic :acquire_release a.b.x + arg2
@atomic :acquire_release a.b.x max arg2
```

Effectuez l'opération binaire exprimée à droite de manière atomique. Stockez le résultat dans le champ du premier argument et renvoyez les valeurs `(old, new)`.

Cette opération se traduit par un appel à `modifyproperty!(a.b, :x, func, arg2)`.

Voir la section [Per-field atomics](@ref man-atomics) dans le manuel pour plus de détails.

# Exemples

```jldoctest
julia> mutable struct Atomic{T}; @atomic x::T; end

julia> a = Atomic(1)
Atomic{Int64}(1)

julia> @atomic a.x # récupère le champ x de a, avec une cohérence séquentielle
1

julia> @atomic :sequentially_consistent a.x = 2 # définit le champ x de a, avec une cohérence séquentielle
2

julia> @atomic a.x += 1 # incrémente le champ x de a, avec une cohérence séquentielle
3

julia> @atomic a.x + 1 # incrémente le champ x de a, avec une cohérence séquentielle
3 => 4

julia> @atomic a.x # récupère le champ x de a, avec une cohérence séquentielle
4

julia> @atomic max(a.x, 10) # change le champ x de a à la valeur maximale, avec une cohérence séquentielle
4 => 10

julia> @atomic a.x max 5 # change à nouveau le champ x de a à la valeur maximale, avec une cohérence séquentielle
10 => 10
```

!!! compat "Julia 1.7"
    Cette fonctionnalité nécessite au moins Julia 1.7.

