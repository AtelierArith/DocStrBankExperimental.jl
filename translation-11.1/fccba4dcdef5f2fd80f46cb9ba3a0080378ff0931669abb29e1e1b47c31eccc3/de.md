```
CholeskyPivoted
```

Matrixfaktorisierungstyp der pivotierten Cholesky-Faktorisation einer dichten symmetrischen/Hermiteschen positiv semi-definiten Matrix `A`. Dies ist der Rückgabetyp von [`cholesky(_, ::RowMaximum)`](@ref), der entsprechenden Matrixfaktorierungsfunktion.

Der triangulierte Cholesky-Faktor kann aus der Faktorisierung `F::CholeskyPivoted` über `F.L` und `F.U` sowie die Permutation über `F.p` erhalten werden, wobei `A[F.p, F.p] ≈ Ur' * Ur ≈ Lr * Lr'` mit `Ur = F.U[1:F.rank, :]` und `Lr = F.L[:, 1:F.rank]` oder alternativ `A ≈ Up' * Up ≈ Lp * Lp'` mit `Up = F.U[1:F.rank, invperm(F.p)]` und `Lp = F.L[invperm(F.p), 1:F.rank]`.

Die folgenden Funktionen sind für `CholeskyPivoted`-Objekte verfügbar: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref) und [`rank`](@ref).

Die Iteration der Zerlegung erzeugt die Komponenten `L` und `U`.

# Beispiele

```jldoctest
julia> X = [1.0, 2.0, 3.0, 4.0];

julia> A = X * X';

julia> C = cholesky(A, RowMaximum(), check = false)
CholeskyPivoted{Float64, Matrix{Float64}, Vector{Int64}}
U-Faktor mit Rang 1:
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 4.0  2.0  3.0  1.0
  ⋅   0.0  6.0  2.0
  ⋅    ⋅   9.0  3.0
  ⋅    ⋅    ⋅   1.0
Permutation:
4-element Vector{Int64}:
 4
 2
 3
 1

julia> C.U[1:C.rank, :]' * C.U[1:C.rank, :] ≈ A[C.p, C.p]
true

julia> l, u = C; # Destrukturierung über Iteration

julia> l == C.L && u == C.U
true
```
