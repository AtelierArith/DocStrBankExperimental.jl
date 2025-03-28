```
sparse_hvcat(rows::Tuple{Vararg{Int}}, values...)
```

Sparse horizontale und vertikale Verkettung in einem Aufruf. Diese Funktion wird für die Blockmatrix-Syntax aufgerufen. Das erste Argument gibt die Anzahl der Argumente an, die in jeder Blockzeile verkettet werden sollen.

!!! compat "Julia 1.8"
    Diese Methode wurde in Julia 1.8 hinzugefügt. Sie ahmt das vorherige Verkettungsverhalten nach, bei dem die Verkettung mit spezialisierten "sparse" Matrizen aus LinearAlgebra.jl automatisch spärliche Ausgaben erzeugte, selbst in Abwesenheit eines SparseArray-Arguments.

