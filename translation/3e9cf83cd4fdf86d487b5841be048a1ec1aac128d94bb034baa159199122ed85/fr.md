```
sum(f, itr; [init])
```

Somme des résultats de l'appel de la fonction `f` sur chaque élément de `itr`.

Le type de retour est `Int` pour les entiers signés de moins de la taille de mot système, et `UInt` pour les entiers non signés de moins de la taille de mot système. Pour tous les autres arguments, un type de retour commun est trouvé auquel tous les arguments sont promus.

La valeur retournée pour un `itr` vide peut être spécifiée par `init`. Elle doit être l'identité additive (c'est-à-dire zéro) car il n'est pas précisé si `init` est utilisé pour des collections non vides.

!!! compat "Julia 1.6"
    L'argument clé `init` nécessite Julia 1.6 ou une version ultérieure.


# Exemples

```jldoctest
julia> sum(abs2, [2; 3; 4])
29
```

Notez la différence importante entre `sum(A)` et `reduce(+, A)` pour les tableaux avec un type d'élément entier petit :

```jldoctest
julia> sum(Int8[100, 28])
128

julia> reduce(+, Int8[100, 28])
-128
```

Dans le premier cas, les entiers sont élargis à la taille de mot système et donc le résultat est 128. Dans le second cas, aucun élargissement n'a lieu et le débordement d'entier entraîne -128.
