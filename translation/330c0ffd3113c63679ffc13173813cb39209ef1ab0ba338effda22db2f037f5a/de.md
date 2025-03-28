```
ColumnNorm
```

Die Spalte mit der maximalen Norm wird für die nachfolgende Berechnung verwendet. Dies wird für die pivotierte QR-Faktorisierung verwendet.

Beachten Sie, dass der [Elementtyp](@ref eltype) der Matrix die Methoden [`norm`](@ref) und [`abs`](@ref) zulassen muss, deren jeweilige Ergebnistypen eine [`<`](@ref) Methode zulassen müssen.
