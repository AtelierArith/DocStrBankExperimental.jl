```
bunchkaufman(A, rook::Bool=false; check = true) -> S::BunchKaufman
```

Berechne die Bunch-Kaufman [^Bunch1977] Faktorisierung einer symmetrischen oder hermiteschen Matrix `A` als `P'*U*D*U'*P` oder `P'*L*D*L'*P`, abhängig davon, welches Dreieck in `A` gespeichert ist, und gebe ein [`BunchKaufman`](@ref) Objekt zurück. Beachte, dass wenn `A` komplex symmetrisch ist, dann `U'` und `L'` die unkonjugierten Transponierten bezeichnen, d.h. `transpose(U)` und `transpose(L)`.

Das Iterieren über die Zerlegung erzeugt die Komponenten `S.D`, `S.U` oder `S.L` je nach dem, was `S.uplo` angibt, und `S.p`.

Wenn `rook` `true` ist, wird Rook-Pivoting verwendet. Wenn `rook` false ist, wird kein Rook-Pivoting verwendet.

Wenn `check = true` ist, wird ein Fehler ausgelöst, wenn die Zerlegung fehlschlägt. Wenn `check = false` ist, liegt die Verantwortung für die Überprüfung der Gültigkeit der Zerlegung (über [`issuccess`](@ref)) beim Benutzer.

Die folgenden Funktionen sind für `BunchKaufman` Objekte verfügbar: [`size`](@ref), `\`, [`inv`](@ref), [`issymmetric`](@ref), [`ishermitian`](@ref), [`getindex`](@ref).

[^Bunch1977]: J R Bunch und L Kaufman, Einige stabile Methoden zur Berechnung der Inertia und zur Lösung symmetrischer linearer Systeme, Mathematics of Computation 31:137 (1977), 163-179. [url](https://www.ams.org/journals/mcom/1977-31-137/S0025-5718-1977-0428694-0/).

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

julia> d, u, p = S; # Destrukturierung durch Iteration

julia> d == S.D && u == S.U && p == S.p
true

julia> S.U*S.D*S.U' - S.P*A*S.P'
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0

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

julia> S.L*S.D*S.L' - A[S.p, S.p]
2×2 Matrix{Float64}:
 0.0  0.0
 0.0  0.0
```
