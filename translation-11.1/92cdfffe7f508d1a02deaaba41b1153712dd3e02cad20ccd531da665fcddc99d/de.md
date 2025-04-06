```
Base.hasfastin(T)
```

Bestimmen Sie, ob die Berechnung `x ∈ collection`, wobei `collection::T` ist, als "schnelle" Operation betrachtet werden kann (typischerweise konstante oder logarithmische Komplexität). Die Definition `hasfastin(x) = hasfastin(typeof(x))` wird zur Bequemlichkeit bereitgestellt, sodass Instanzen anstelle von Typen übergeben werden können. Die Form, die ein Typ-Argument akzeptiert, sollte jedoch für neue Typen definiert werden.

Der Standardwert für `hasfastin(T)` ist `true` für Subtypen von [`AbstractSet`](@ref), [`AbstractDict`](@ref) und [`AbstractRange`](@ref) und `false` andernfalls.
