```
\(A, B)
```

Matrixdivision mit einem Polyalgorithmus. Für die Eingabematrizen `A` und `B` ist das Ergebnis `X` so beschaffen, dass `A*X == B`, wenn `A` quadratisch ist. Der verwendete Solver hängt von der Struktur von `A` ab. Wenn `A` ober- oder unterdreieckig (oder diagonal) ist, ist keine Faktorisierung von `A` erforderlich und das System wird mit Vorwärts- oder Rückwärtssubstitution gelöst. Für nicht-triangular quadratische Matrizen wird eine LU-Faktorisierung verwendet.

Für rechteckige `A` ist das Ergebnis die Lösung der minimalen Norm der kleinsten Quadrate, die durch eine pivotierte QR-Faktorisierung von `A` und eine Rangschätzung von `A` basierend auf dem R-Faktor berechnet wird.

Wenn `A` spärlich ist, wird ein ähnlicher Polyalgorithmus verwendet. Für indefiniten Matrizen verwendet die `LDLt`-Faktorisierung während der numerischen Faktorisierung kein Pivoting, und daher kann das Verfahren selbst bei invertierbaren Matrizen fehlschlagen.

Siehe auch: [`factorize`](@ref), [`pinv`](@ref).

# Beispiele

```jldoctest
julia> A = [1 0; 1 -2]; B = [32; -4];

julia> X = A \ B
2-element Vector{Float64}:
 32.0
 18.0

julia> A * X == B
true
```
