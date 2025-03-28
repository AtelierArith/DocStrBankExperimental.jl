```
sizehint!(s, n; first::Bool=false, shrink::Bool=true) -> s
```

Suggérez que la collection `s` réserve une capacité d'au moins `n` éléments. C'est-à-dire que si vous vous attendez à devoir ajouter beaucoup de valeurs à `s`, vous pouvez éviter le coût de la réallocation incrémentale en le faisant une fois au départ ; cela peut améliorer les performances.

Si `first` est `true`, alors tout espace supplémentaire est réservé avant le début de la collection. De cette façon, les appels ultérieurs à `pushfirst!` (au lieu de `push!`) peuvent devenir plus rapides. Fournir ce mot-clé peut entraîner une erreur si la collection n'est pas ordonnée ou si `pushfirst!` n'est pas pris en charge pour cette collection.

Si `shrink=true` (par défaut), la capacité de la collection peut être réduite si sa capacité actuelle est supérieure à `n`.

Voir aussi [`resize!`](@ref).

# Remarques sur le modèle de performance

Pour les types qui prennent en charge `sizehint!`,

1. Les méthodes `push!` et `append!` peuvent généralement (mais ne sont pas tenues de) préallouer un stockage supplémentaire. Pour les types implémentés dans `Base`, elles le font généralement, en utilisant une heuristique optimisée pour un cas d'utilisation général.
2. `sizehint!` peut contrôler cette préallocation. Encore une fois, cela le fait généralement pour les types dans `Base`.
3. `empty!` est presque sans coût (et O(1)) pour les types qui prennent en charge ce type de préallocation.

!!! compat "Julia 1.11"
    Les arguments `shrink` et `first` ont été ajoutés dans Julia 1.11.

