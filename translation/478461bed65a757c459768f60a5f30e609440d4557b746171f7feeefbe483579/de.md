```
SVD <: Faktorisierung
```

Matrixfaktorisierungstyp der singulären Wertzerlegung (SVD) einer Matrix `A`. Dies ist der Rückgabetyp von [`svd(_)`](@ref), der entsprechenden Matrixfaktorisierungsfunktion.

Wenn `F::SVD` das Faktorisierungsobjekt ist, können `U`, `S`, `V` und `Vt` über `F.U`, `F.S`, `F.V` und `F.Vt` abgerufen werden, sodass `A = U * Diagonal(S) * Vt`. Die singulären Werte in `S` sind in absteigender Reihenfolge sortiert.

Das Iterieren über die Zerlegung erzeugt die Komponenten `U`, `S` und `V`.

# Beispiele

```jldoctest
julia> A = [1. 0. 0. 0. 2.; 0. 0. 3. 0. 0.; 0. 0. 0. 0. 0.; 0. 2. 0. 0. 0.]
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> F = svd(A)
SVD{Float64, Float64, Matrix{Float64}, Vector{Float64}}
U-Faktor:
4×4 Matrix{Float64}:
 0.0  1.0   0.0  0.0
 1.0  0.0   0.0  0.0
 0.0  0.0   0.0  1.0
 0.0  0.0  -1.0  0.0
singuläre Werte:
4-element Vector{Float64}:
 3.0
 2.23606797749979
 2.0
 0.0
Vt-Faktor:
4×5 Matrix{Float64}:
 -0.0        0.0  1.0  -0.0  0.0
  0.447214   0.0  0.0   0.0  0.894427
  0.0       -1.0  0.0   0.0  0.0
  0.0        0.0  0.0   1.0  0.0

julia> F.U * Diagonal(F.S) * F.Vt
4×5 Matrix{Float64}:
 1.0  0.0  0.0  0.0  2.0
 0.0  0.0  3.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  2.0  0.0  0.0  0.0

julia> u, s, v = F; # Destrukturierung über Iteration

julia> u == F.U && s == F.S && v == F.V
true
```
