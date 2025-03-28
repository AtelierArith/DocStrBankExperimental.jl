```
lu!(A, pivot = RowMaximum(); check = true, allowsingular = false) -> LU
```

`lu!` ist dasselbe wie [`lu`](@ref), speichert jedoch Platz, indem es die Eingabe `A` überschreibt, anstatt eine Kopie zu erstellen. Eine [`InexactError`](@ref) Ausnahme wird ausgelöst, wenn die Faktorisierung eine Zahl produziert, die vom Elementtyp von `A` nicht darstellbar ist, z. B. für Ganzzahltypen.

!!! compat "Julia 1.11"
    Das Schlüsselwortargument `allowsingular` wurde in Julia 1.11 hinzugefügt.


# Beispiele

```jldoctest
julia> A = [4. 3.; 6. 3.]
2×2 Matrix{Float64}:
 4.0  3.0
 6.0  3.0

julia> F = lu!(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L-Faktor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U-Faktor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> iA = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> lu!(iA)
ERROR: InexactError: Int64(0.6666666666666666)
Stacktrace:
[...]
```
