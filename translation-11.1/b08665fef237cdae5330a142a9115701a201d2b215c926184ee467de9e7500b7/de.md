```
qr!(A, pivot = NoPivot(); blocksize)
```

`qr!` ist dasselbe wie [`qr`](@ref), wenn `A` ein Subtyp von [`AbstractMatrix`](@ref) ist, speichert jedoch Platz, indem es die Eingabe `A` überschreibt, anstatt eine Kopie zu erstellen. Eine [`InexactError`](@ref) Ausnahme wird ausgelöst, wenn die Faktorisierung eine Zahl produziert, die vom Elementtyp von `A` nicht darstellbar ist, z. B. für Ganzzahltypen.

!!! compat "Julia 1.4"
    Das Schlüsselwortargument `blocksize` erfordert Julia 1.4 oder höher.


# Beispiele

```jldoctest
julia> a = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> qr!(a)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q-Faktor: 2×2 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R-Faktor:
2×2 Matrix{Float64}:
 -3.16228  -4.42719
  0.0      -0.632456

julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> qr!(a)
ERROR: InexactError: Int64(3.1622776601683795)
Stacktrace:
[...]
```
