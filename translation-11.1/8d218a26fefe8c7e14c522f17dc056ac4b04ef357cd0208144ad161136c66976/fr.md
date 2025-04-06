```
isunordered(x)
```

Retourne `true` si `x` est une valeur qui n'est pas ordonnable selon [`<`](@ref), comme `NaN` ou `missing`.

Les valeurs qui évaluent à `true` avec ce prédicat peuvent être ordonnables par rapport à d'autres ordres tels que [`isless`](@ref).

!!! compat "Julia 1.7"
    Cette fonction nécessite Julia 1.7 ou une version ultérieure.

