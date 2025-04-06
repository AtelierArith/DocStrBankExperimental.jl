```
minimum(itr; [init])
```

Retourne le plus petit élément d'une collection.

La valeur retournée pour un `itr` vide peut être spécifiée par `init`. Cela doit être un élément neutre pour `min` (c'est-à-dire qui est supérieur ou égal à tout autre élément) car il n'est pas précisé si `init` est utilisé pour des collections non vides.

!!! compat "Julia 1.6"
    L'argument clé `init` nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> minimum(-20.5:10)
-20.5

julia> minimum([1,2,3])
1

julia> minimum([])
ERROR: ArgumentError: reducing over an empty collection is not allowed; consider supplying `init` to the reducer
Stacktrace:
[...]

julia> minimum([]; init=Inf)
Inf
```
