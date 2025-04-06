```
prod(f, itr; [init])
```

Renvoie le produit de `f` appliqué à chaque élément de `itr`.

Le type de retour est `Int` pour les entiers signés de moins de la taille de mot système, et `UInt` pour les entiers non signés de moins de la taille de mot système. Pour tous les autres arguments, un type de retour commun est trouvé auquel tous les arguments sont promus.

La valeur renvoyée pour un `itr` vide peut être spécifiée par `init`. Elle doit être l'identité multiplicative (c'est-à-dire un) car il n'est pas spécifié si `init` est utilisé pour des collections non vides.

!!! compat "Julia 1.6"
    L'argument clé `init` nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> prod(abs2, [2; 3; 4])
576
```
