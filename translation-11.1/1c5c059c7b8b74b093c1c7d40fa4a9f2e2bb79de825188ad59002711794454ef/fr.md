```
IndexCartesian()
```

Sous-type de [`IndexStyle`](@ref) utilisé pour décrire les tableaux qui sont indexés de manière optimale par un index cartésien. C'est le comportement par défaut pour les nouveaux sous-types personnalisés [`AbstractArray`](@ref).

Un style d'indexation cartésien utilise plusieurs indices entiers pour décrire la position dans un tableau multidimensionnel, avec exactement un indice par dimension. Cela signifie que demander [`eachindex`](@ref) à partir d'un tableau qui est `IndexCartesian` renverra une plage de [`CartesianIndices`](@ref).

Un tableau personnalisé de dimension `N` qui rapporte son `IndexStyle` comme `IndexCartesian` doit implémenter l'indexation (et l'assignation indexée) avec exactement `N` indices `Int` ; toutes les autres expressions d'indexation — y compris l'indexation linéaire — seront recalculées à l'emplacement cartésien équivalent. Par exemple, si `A` était une matrice personnalisée `2×3` avec indexation cartésienne, et que nous référencions `A[5]`, cela serait recalculé à l'indice cartésien équivalent et appellerait `A[1, 3]` puisque `5 = 1 + 2*(3 - 1)`.

Il est significativement plus coûteux de calculer des indices cartésiens à partir d'un indice linéaire que d'aller dans l'autre sens. La première opération nécessite une division — une opération très coûteuse — tandis que la seconde n'utilise que la multiplication et l'addition et est essentiellement gratuite. Cette asymétrie signifie qu'il est beaucoup plus coûteux d'utiliser l'indexation linéaire avec un tableau `IndexCartesian` qu'il ne l'est d'utiliser l'indexation cartésienne avec un tableau `IndexLinear`.

Voir aussi [`IndexLinear`](@ref).
