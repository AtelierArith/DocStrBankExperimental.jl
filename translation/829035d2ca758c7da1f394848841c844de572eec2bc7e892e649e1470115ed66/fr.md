```
IndexLinear()
```

Sous-type de [`IndexStyle`](@ref) utilisé pour décrire les tableaux qui sont indexés de manière optimale par un index linéaire.

Un style d'indexation linéaire utilise un index entier pour décrire la position dans le tableau (même s'il s'agit d'un tableau multidimensionnel) et un ordre de colonne est utilisé pour accéder efficacement aux éléments. Cela signifie que la demande de [`eachindex`](@ref) à partir d'un tableau qui est `IndexLinear` renverra une simple plage unidimensionnelle, même s'il est multidimensionnel.

Un tableau personnalisé qui signale son `IndexStyle` comme `IndexLinear` n'a besoin d'implémenter l'indexation (et l'assignation indexée) qu'avec un seul index `Int` ; toutes les autres expressions d'indexation — y compris les accès multidimensionnels — seront recomputées à l'index linéaire. Par exemple, si `A` était une matrice personnalisée `2×3` avec indexation linéaire, et que nous référencions `A[1, 3]`, cela serait recomputé à l'index linéaire équivalent et appellerait `A[5]` puisque `1 + 2*(3 - 1) = 5`.

Voir aussi [`IndexCartesian`](@ref).
