```
*(A, B::AbstractMatrix, C)
A * B * C * D
```

Die verkettete Multiplikation von 3 oder 4 Matrizen erfolgt in der effizientesten Reihenfolge, basierend auf den Größen der Arrays. Das heißt, die Anzahl der benötigten skalaren Multiplikationen für `(A * B) * C` (mit 3 dichten Matrizen) wird mit der für `A * (B * C)` verglichen, um zu entscheiden, welche dieser beiden Ausdrücke ausgeführt werden soll.

Wenn der letzte Faktor ein Vektor ist oder der erste ein transponierter Vektor, ist es effizient, diese zuerst zu behandeln. Insbesondere bedeutet `x' * B * y`, dass `(x' * B) * y` für eine gewöhnliche spaltenmajorisierte `B::Matrix`. Im Gegensatz zu `dot(x, B, y)` wird dabei ein Zwischenarray alloziert.

Wenn der erste oder letzte Faktor eine Zahl ist, wird dies mit der Matrizenmultiplikation fusioniert, unter Verwendung von 5-arg [`mul!`](@ref).

Siehe auch [`muladd`](@ref), [`dot`](@ref).

!!! compat "Julia 1.7"
    Diese Optimierungen erfordern mindestens Julia 1.7.

