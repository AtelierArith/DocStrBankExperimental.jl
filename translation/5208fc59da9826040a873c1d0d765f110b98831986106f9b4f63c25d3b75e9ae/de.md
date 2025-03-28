```
cholesky(A, NoPivot(); check = true) -> Cholesky
```

Berechnen Sie die Cholesky-Zerlegung einer dichten symmetrischen positiv definiten Matrix `A` und geben Sie eine [`Cholesky`](@ref) Zerlegung zurück. Die Matrix `A` kann entweder eine [`Symmetric`](@ref) oder [`Hermitian`](@ref) [`AbstractMatrix`](@ref) oder eine *perfekt* symmetrische oder hermitische `AbstractMatrix` sein.

Der dreieckige Cholesky-Faktor kann aus der Zerlegung `F` über `F.L` und `F.U` erhalten werden, wobei `A ≈ F.U' * F.U ≈ F.L * F.L'`.

Die folgenden Funktionen sind für `Cholesky`-Objekte verfügbar: [`size`](@ref), [`\`](@ref), [`inv`](@ref), [`det`](@ref), [`logdet`](@ref) und [`isposdef`](@ref).

Wenn Sie eine Matrix `A` haben, die aufgrund von Rundungsfehlern bei ihrer Konstruktion leicht nicht-hermitisch ist, wickeln Sie sie in `Hermitian(A)` ein, bevor Sie sie an `cholesky` übergeben, um sie als perfekt hermitisch zu behandeln.

Wenn `check = true`, wird ein Fehler ausgelöst, wenn die Zerlegung fehlschlägt. Wenn `check = false`, liegt die Verantwortung für die Überprüfung der Gültigkeit der Zerlegung (über [`issuccess`](@ref)) beim Benutzer.

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
```
