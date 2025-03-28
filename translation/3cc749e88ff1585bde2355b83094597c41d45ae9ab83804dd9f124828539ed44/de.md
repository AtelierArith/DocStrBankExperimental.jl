```
Cholesky <: Faktorisierung
```

Matrixfaktorisierungstyp der Cholesky-Faktorisierung einer dichten symmetrischen/Hermiteschen positiv definiten Matrix `A`. Dies ist der Rückgabetyp von [`cholesky`](@ref), der entsprechenden Matrixfaktorisierungsfunktion.

Der dreieckige Cholesky-Faktor kann aus der Faktorisierung `F::Cholesky` über `F.L` und `F.U` erhalten werden, wobei `A ≈ F.U' * F.U ≈ F.L * F.L'`.

Die folgenden Funktionen sind für `Cholesky`-Objekte verfügbar: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), [`logdet`](@ref) und [`isposdef`](@ref).

Das Iterieren über die Zerlegung erzeugt die Komponenten `L` und `U`.

# Beispiele

```jldoctest
julia> A = [4. 12. -16.; 12. 37. -43.; -16. -43. 98.]
3×3 Matrix{Float64}:
   4.0   12.0  -16.0
  12.0   37.0  -43.0
 -16.0  -43.0   98.0

julia> C = cholesky(A)
Cholesky{Float64, Matrix{Float64}}
U-Faktor:
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.U
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.L
3×3 LowerTriangular{Float64, Matrix{Float64}}:
  2.0   ⋅    ⋅
  6.0  1.0   ⋅
 -8.0  5.0  3.0

julia> C.L * C.U == A
true

julia> l, u = C; # Destrukturierung über Iteration

julia> l == C.L && u == C.U
true
```
