```
isunordered(x)
```

Gibt `true` zurück, wenn `x` ein Wert ist, der nicht nach [`<`](@ref) ordnungsfähig ist, wie `NaN` oder `missing`.

Die Werte, die mit diesem Prädikat zu `true` ausgewertet werden, können in Bezug auf andere Ordnungen wie [`isless`](@ref) ordnungsfähig sein.

!!! compat "Julia 1.7"
    Diese Funktion erfordert Julia 1.7 oder höher.

