```
typeintersect(T::Type, S::Type)
```

Calcule un type qui contient l'intersection de `T` et `S`. En général, ce sera le plus petit type de ce type ou un proche de celui-ci.

Un cas spécial où un comportement exact est garanti : lorsque `T <: S`, `typeintersect(S, T) == T == typeintersect(T, S)`.
