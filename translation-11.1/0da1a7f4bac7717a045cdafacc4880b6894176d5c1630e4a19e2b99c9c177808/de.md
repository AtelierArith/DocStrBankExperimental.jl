```
cholesky!(A::AbstractMatrix, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

Das gleiche wie [`cholesky`](@ref), aber spart Speicherplatz, indem es die Eingabe `A` überschreibt, anstatt eine Kopie zu erstellen. Eine [`InexactError`](@ref) Ausnahme wird ausgelöst, wenn die Faktorisierung eine Zahl produziert, die vom Elementtyp von `A` nicht darstellbar ist, z. B. für Ganzzahltypen.
