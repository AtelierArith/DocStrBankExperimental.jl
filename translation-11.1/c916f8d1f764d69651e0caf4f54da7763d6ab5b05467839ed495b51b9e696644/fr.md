```
extrema(f, itr; [init]) -> (mn, mx)
```

Calculez à la fois le minimum `mn` et le maximum `mx` de `f` appliqué à chaque élément de `itr` et renvoyez-les sous forme de tuple de 2 éléments. Une seule passe est effectuée sur `itr`.

La valeur renvoyée pour un `itr` vide peut être spécifiée par `init`. Cela doit être un tuple de 2 éléments dont le premier et le deuxième éléments sont des éléments neutres pour `min` et `max` respectivement (c'est-à-dire qui sont supérieurs/inférieurs ou égaux à tout autre élément). Il est utilisé pour des collections non vides. Remarque : cela implique que, pour un `itr` vide, la valeur renvoyée `(mn, mx)` satisfait `mn ≥ mx` même si pour un `itr` non vide, elle satisfait `mn ≤ mx`. C'est un résultat "paradoxal" mais néanmoins attendu.

!!! compat "Julia 1.2"
    Cette méthode nécessite Julia 1.2 ou une version ultérieure.


!!! compat "Julia 1.8"
    L'argument clé `init` nécessite Julia 1.8 ou une version ultérieure.


# Exemples

```jldoctest
julia> extrema(sin, 0:π)
(0.0, 0.9092974268256817)

julia> extrema(sin, Real[]; init = (1.0, -1.0))  # bon, puisque -1 ≤ sin(::Real) ≤ 1
(1.0, -1.0)
```
