```
Base.hasfastin(T)
```

Déterminez si le calcul `x ∈ collection` où `collection::T` peut être considéré comme une opération "rapide" (typiquement de complexité constante ou logarithmique). La définition `hasfastin(x) = hasfastin(typeof(x))` est fournie pour la commodité afin que des instances puissent être passées au lieu de types. Cependant, la forme qui accepte un argument de type doit être définie pour les nouveaux types.

La valeur par défaut pour `hasfastin(T)` est `true` pour les sous-types de [`AbstractSet`](@ref), [`AbstractDict`](@ref) et [`AbstractRange`](@ref) et `false` sinon.
