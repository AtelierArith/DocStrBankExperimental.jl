```
eigen!(A; permute, scale, sortby)
eigen!(A, B; sortby)
```

Identique à [`eigen`](@ref), mais économise de l'espace en écrasant l'entrée `A` (et `B`), au lieu de créer une copie.
