```
prod(itr; [init])
```

Retourne le produit de tous les éléments d'une collection.

Le type de retour est `Int` pour les entiers signés de moins que la taille de mot système, et `UInt` pour les entiers non signés de moins que la taille de mot système. Pour tous les autres arguments, un type de retour commun est trouvé auquel tous les arguments sont promus.

La valeur retournée pour un `itr` vide peut être spécifiée par `init`. Elle doit être l'identité multiplicative (c'est-à-dire un) car il n'est pas spécifié si `init` est utilisé pour des collections non vides.

!!! compat "Julia 1.6"
    L'argument clé `init` nécessite Julia 1.6 ou une version ultérieure.


Voir aussi : [`reduce`](@ref), [`cumprod`](@ref), [`any`](@ref).

# Exemples

```jldoctest
julia> prod(1:5)
120

julia> prod(1:5; init = 1.0)
120.0
```
