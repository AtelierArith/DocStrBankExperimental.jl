```
LU <: Faktorisierung
```

Matrixfaktorisierungstyp der `LU`-Faktorisierung einer quadratischen Matrix `A`. Dies ist der Rückgabetyp von [`lu`](@ref), der entsprechenden Matrixfaktorisierungsfunktion.

Die einzelnen Komponenten der Faktorisierung `F::LU` können über [`getproperty`](@ref) zugegriffen werden:

| Komponente | Beschreibung                                      |
|:---------- |:------------------------------------------------- |
| `F.L`      | `L` (einheitsuntere Dreiecksmatrix) Teil von `LU` |
| `F.U`      | `U` (obere Dreiecksmatrix) Teil von `LU`          |
| `F.p`      | (rechte) Permutations-`Vector`                    |
| `F.P`      | (rechte) Permutations-`Matrix`                    |

Das Iterieren über die Faktorisierung erzeugt die Komponenten `F.L`, `F.U` und `F.p`.

# Beispiele

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L-Faktor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U-Faktor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # Destrukturierung über Iteration

julia> l == F.L && u == F.U && p == F.p
true
```
