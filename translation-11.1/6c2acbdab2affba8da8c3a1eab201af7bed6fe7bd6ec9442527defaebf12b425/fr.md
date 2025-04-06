```
isless(x, y)
```

Testez si `x` est inférieur à `y`, selon un ordre total fixe (défini avec [`isequal`](@ref)). `isless` n'est pas défini pour les paires `(x, y)` de tous types. Cependant, s'il est défini, il est censé satisfaire les conditions suivantes :

  * Si `isless(x, y)` est défini, alors `isless(y, x)` et `isequal(x, y)` le sont aussi, et exactement l'un de ces trois renvoie `true`.
  * La relation définie par `isless` est transitive, c'est-à-dire que `isless(x, y) && isless(y, z)` implique `isless(x, z)`.

Les valeurs qui sont normalement non ordonnées, comme `NaN`, sont ordonnées après les valeurs régulières. Les valeurs [`missing`](@ref) sont ordonnées en dernier.

C'est la comparaison par défaut utilisée par [`sort!`](@ref).

# Implémentation

Les types non numériques avec un ordre total devraient implémenter cette fonction. Les types numériques n'ont besoin de l'implémenter que s'ils ont des valeurs spéciales telles que `NaN`. Les types avec un ordre partiel devraient implémenter [`<`](@ref). Consultez la documentation sur [Ordres Alternatifs](@ref) pour savoir comment définir des méthodes d'ordre alternatives qui peuvent être utilisées dans le tri et les fonctions connexes.

# Exemples

```jldoctest
julia> isless(1, 3)
true

julia> isless("Red", "Blue")
false
```
