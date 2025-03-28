```
SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
```

Vektortyp für die Speicherung von spärlichen Vektoren. Kann erstellt werden, indem die Länge des Vektors, ein *sortierter* Vektor von Nicht-Null-Indizes und ein Vektor von Nicht-Null-Werten übergeben werden.

Zum Beispiel kann der Vektor `[5, 6, 0, 7]` dargestellt werden als

```julia
SparseVector(4, [1, 2, 4], [5, 6, 7])
```

Dies zeigt an, dass das Element an Index 1 5 ist, an Index 2 6 ist, an Index 3 `zero(Int)` ist und an Index 4 7 ist.

Es kann bequemer sein, spärliche Vektoren direkt aus dichten Vektoren mit `sparse` zu erstellen, da

```julia
sparse([5, 6, 0, 7])
```

den gleichen spärlichen Vektor ergibt.
