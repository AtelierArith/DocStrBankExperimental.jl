```
sum(itr; [init])
```

Retourne la somme de tous les éléments d'une collection.

Le type de retour est `Int` pour les entiers signés de moins que la taille de mot système, et `UInt` pour les entiers non signés de moins que la taille de mot système. Pour tous les autres arguments, un type de retour commun est trouvé auquel tous les arguments sont promus.

La valeur retournée pour un `itr` vide peut être spécifiée par `init`. Elle doit être l'identité additive (c'est-à-dire zéro) car il n'est pas spécifié si `init` est utilisé pour des collections non vides.

!!! compat "Julia 1.6"
    L'argument clé `init` nécessite Julia 1.6 ou une version ultérieure.


Voir aussi : [`reduce`](@ref), [`mapreduce`](@ref), [`count`](@ref), [`union`](@ref).

# Exemples

```jldoctest
julia> sum(1:20)
210

julia> sum(1:20; init = 0.0)
210.0
```
