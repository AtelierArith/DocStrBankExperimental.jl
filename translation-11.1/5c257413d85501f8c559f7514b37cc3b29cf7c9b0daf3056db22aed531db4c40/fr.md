```
cumprod!(B, A; dims::Integer)
```

Produit cumulatif de `A` le long de la dimension `dims`, stockant le résultat dans `B`. Voir aussi [`cumprod`](@ref).

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.

