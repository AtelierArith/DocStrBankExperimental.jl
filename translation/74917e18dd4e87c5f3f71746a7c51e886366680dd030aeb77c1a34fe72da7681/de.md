```
RowNonZero
```

Das erste von null verschiedene Element in den verbleibenden Zeilen wird als Pivot-Element gewählt.

Seien Sie vorsichtig, dass der resultierende LU-Algorithmus für Gleitkomma-Matrizen numerisch instabil ist — diese Strategie ist hauptsächlich nützlich für den Vergleich mit Handberechnungen (die typischerweise diese Strategie verwenden) oder für andere algebraische Typen (z. B. rationale Zahlen), die nicht anfällig für Rundungsfehler sind. Andernfalls sollte die Standard-Pivotierungsstrategie `RowMaximum` im Allgemeinen bei der Gauß-Elimination bevorzugt werden.

Beachten Sie, dass der [Elementtyp](@ref eltype) der Matrix eine [`iszero`](@ref) Methode unterstützen muss.
