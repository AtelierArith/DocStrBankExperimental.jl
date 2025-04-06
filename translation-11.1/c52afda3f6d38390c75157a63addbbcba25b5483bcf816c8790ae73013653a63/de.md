```
similar(A::AbstractSparseMatrixCSC{Tv,Ti}, [::Type{TvNew}, ::Type{TiNew}, m::Integer, n::Integer]) where {Tv,Ti}
```

Erstellt ein nicht initialisiertes veränderliches Array mit dem angegebenen Elementtyp, Indextyp und der Größe, basierend auf der gegebenen Quelle `SparseMatrixCSC`. Die neue spärliche Matrix behält die Struktur der ursprünglichen spärlichen Matrix bei, es sei denn, die Dimensionen der Ausgabematrix unterscheiden sich von der Ausgabe.

Die Ausgabematrix hat Nullen an denselben Stellen wie die Eingabe, aber nicht initialisierte Werte für die nicht nullen Stellen.
