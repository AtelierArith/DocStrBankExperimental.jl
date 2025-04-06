```
sparse_vcat(A...)
```

Verkettet entlang Dimension 1. Gibt ein SparseMatrixCSC-Objekt zurück.

!!! compat "Julia 1.8"
    Diese Methode wurde in Julia 1.8 hinzugefügt. Sie ahmt das frühere Verhaltensmuster der Verkettung nach, bei dem die Verkettung mit spezialisierten "sparse" Matrizenarten aus LinearAlgebra.jl automatisch spärliche Ausgaben erzeugte, selbst in Abwesenheit eines SparseArray-Arguments.

