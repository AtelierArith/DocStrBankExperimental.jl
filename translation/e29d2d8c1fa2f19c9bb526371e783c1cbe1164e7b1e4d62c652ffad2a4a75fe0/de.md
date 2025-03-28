```
RowMaximum
```

Das Element mit der maximalen Größe in den verbleibenden Zeilen wird als Pivot-Element gewählt. Dies ist die Standardstrategie für die LU-Faktorisierung von Gleitkommazahlen und wird manchmal als der "partielle Pivotierungs"-Algorithmus bezeichnet.

Beachten Sie, dass der [Elementtyp](@ref eltype) der Matrix eine [`abs`](@ref)-Methode unterstützen muss, deren Ergebnistyp eine [`<`](@ref)-Methode unterstützen muss.
