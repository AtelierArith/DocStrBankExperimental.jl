```
typeintersect(T::Type, S::Type)
```

Calcula un tipo que contiene la intersección de `T` y `S`. Normalmente, este será el tipo más pequeño o uno cercano a él.

Un caso especial donde se garantiza un comportamiento exacto: cuando `T <: S`, `typeintersect(S, T) == T == typeintersect(T, S)`.
