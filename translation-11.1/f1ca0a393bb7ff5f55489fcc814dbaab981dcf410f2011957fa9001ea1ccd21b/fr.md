```
extrema(itr; [init]) -> (mn, mx)
```

Calculez à la fois l'élément minimum `mn` et l'élément maximum `mx` en un seul passage, et renvoyez-les sous forme de tuple de 2 éléments.

La valeur renvoyée pour un `itr` vide peut être spécifiée par `init`. Cela doit être un tuple de 2 éléments dont le premier et le deuxième éléments sont des éléments neutres pour `min` et `max` respectivement (c'est-à-dire qui sont supérieurs/inférieurs ou égaux à tout autre élément). En conséquence, lorsque `itr` est vide, le tuple renvoyé `(mn, mx)` satisfera `mn ≥ mx`. Lorsque `init` est spécifié, il peut être utilisé même pour un `itr` non vide.

!!! compat "Julia 1.8"
    L'argument clé `init` nécessite Julia 1.8 ou une version ultérieure.


# Exemples

```jldoctest
julia> extrema(2:10)
(2, 10)

julia> extrema([9,pi,4.5])
(3.141592653589793, 9.0)

julia> extrema([]; init = (Inf, -Inf))
(Inf, -Inf)
```
