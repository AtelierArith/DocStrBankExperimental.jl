```
maximum(itr; [init])
```

Retourne le plus grand élément d'une collection.

La valeur retournée pour un `itr` vide peut être spécifiée par `init`. Cela doit être un élément neutre pour `max` (c'est-à-dire qui est inférieur ou égal à tout autre élément) car il n'est pas précisé si `init` est utilisé pour des collections non vides.

!!! compat "Julia 1.6"
    L'argument clé `init` nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> maximum(-20.5:10)
9.5

julia> maximum([1,2,3])
3

julia> maximum(())
ERROR: ArgumentError: réduire sur une collection vide n'est pas autorisé ; envisagez de fournir `init` au réducteur
Stacktrace:
[...]

julia> maximum((); init=-Inf)
-Inf
```
