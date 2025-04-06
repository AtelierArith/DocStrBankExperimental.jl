```
cumsum!(B, A; dims::Integer)
```

Somme cumulative de `A` le long de la dimension `dims`, stockant le résultat dans `B`. Voir aussi [`cumsum`](@ref).

!!! warning
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.

