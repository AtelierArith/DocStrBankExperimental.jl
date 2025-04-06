```
minimum(f, itr; [init])
```

Retourne le plus petit résultat de l'appel de la fonction `f` sur chaque élément de `itr`.

La valeur retournée pour un `itr` vide peut être spécifiée par `init`. Cela doit être un élément neutre pour `min` (c'est-à-dire qui est supérieur ou égal à tout autre élément) car il n'est pas spécifié si `init` est utilisé pour des collections non vides.

!!! compat "Julia 1.6"
    L'argument clé `init` nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> minimum(length, ["Julion", "Julia", "Jule"])
4

julia> minimum(length, []; init=typemax(Int64))
9223372036854775807

julia> minimum(sin, Real[]; init=1.0)  # bon, puisque la sortie de sin est <= 1
1.0
```
