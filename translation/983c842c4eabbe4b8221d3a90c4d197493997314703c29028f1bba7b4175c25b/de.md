```
BunchKaufman <: Faktorisierung
```

Matrixfaktorisierungstyp der Bunch-Kaufman-Faktorisierung einer symmetrischen oder hermiteschen Matrix `A` als `P'UDU'P` oder `P'LDL'P`, abhängig davon, ob das obere (der Standard) oder das untere Dreieck in `A` gespeichert ist. Wenn `A` komplex symmetrisch ist, dann bezeichnen `U'` und `L'` die unkonjugierten Transponierten, d.h. `transpose(U)` und `transpose(L)`, jeweils. Dies ist der Rückgabetyp von [`bunchkaufman`](@ref), der entsprechenden Matrixfaktorisierungsfunktion.

Wenn `S::BunchKaufman` das Faktorisierungsobjekt ist, können die Komponenten über `S.D`, `S.U` oder `S.L` je nach `S.uplo` und `S.p` abgerufen werden.

Das Iterieren über die Zerlegung erzeugt die Komponenten `S.D`, `S.U` oder `S.L` je nach `S.uplo` und `S.p`.

# Beispiele

```jldoctest
julia> A = Float64.([1 2; 2 3])
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  3.0

julia> S = bunchkaufman(A) # A wird intern von Symmetric(A) umschlossen
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D-Faktor:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 -0.333333  0.0
  0.0       3.0
U-Faktor:
2×2 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.666667
  ⋅   1.0
Permutation:
2-element Vector{Int64}:
 1
 2

julia> d, u, p = S; # Destrukturierung über Iteration

julia> d == S.D && u == S.U && p == S.p
true

julia> S = bunchkaufman(Symmetric(A, :L))
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D-Faktor:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 3.0   0.0
 0.0  -0.333333
L-Faktor:
2×2 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0        ⋅
 0.666667  1.0
Permutation:
2-element Vector{Int64}:
 2
 1
```
