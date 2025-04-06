```
maximum(f, itr; [init])
```

Retourne le plus grand résultat de l'appel de la fonction `f` sur chaque élément de `itr`.

La valeur retournée pour un `itr` vide peut être spécifiée par `init`. Cela doit être un élément neutre pour `max` (c'est-à-dire qui est inférieur ou égal à tout autre élément) car il n'est pas spécifié si `init` est utilisé pour des collections non vides.

!!! compat "Julia 1.6"
    L'argument clé `init` nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> maximum(length, ["Julion", "Julia", "Jule"])
6

julia> maximum(length, []; init=-1)
-1

julia> maximum(sin, Real[]; init=-1.0)  # bon, puisque la sortie de sin est >= -1
-1.0
```
