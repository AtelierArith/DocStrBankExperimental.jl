```
cholesky!(A::AbstractMatrix, NoPivot(); check = true) -> Cholesky
```

Das gleiche wie [`cholesky`](@ref), aber spart Speicher, indem es die Eingabe `A` überschreibt, anstatt eine Kopie zu erstellen. Eine [`InexactError`](@ref) Ausnahme wird ausgelöst, wenn die Faktorisierung eine Zahl produziert, die vom Elementtyp von `A` nicht darstellbar ist, z. B. für Ganzzahltypen.

# Beispiele

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> cholesky!(A)
ERROR: InexactError: Int64(6.782329983125268)
Stacktrace:
[...]
```
