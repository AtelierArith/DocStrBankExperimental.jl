```
qr(A, pivot = NoPivot(); blocksize) -> F
```

Berechne die QR-Zerlegung der Matrix `A`: eine orthogonale (oder unitäre, wenn `A` komplexwertig ist) Matrix `Q` und eine obere Dreiecksmatrix `R`, sodass

$$
A = Q R
$$

Das zurückgegebene Objekt `F` speichert die Zerlegung in einem kompakten Format:

  * wenn `pivot == ColumnNorm()` dann ist `F` ein [`QRPivoted`](@ref) Objekt,
  * andernfalls, wenn der Elementtyp von `A` ein BLAS-Typ ist ([`Float32`](@ref), [`Float64`](@ref), `ComplexF32` oder `ComplexF64`), dann ist `F` ein [`QRCompactWY`](@ref) Objekt,
  * andernfalls ist `F` ein [`QR`](@ref) Objekt.

Die einzelnen Komponenten der Zerlegung `F` können über Eigenschaftsaccessoren abgerufen werden:

  * `F.Q`: die orthogonale/unitäre Matrix `Q`
  * `F.R`: die obere Dreiecksmatrix `R`
  * `F.p`: der Permutationsvektor des Pivots ([`QRPivoted`](@ref) nur)
  * `F.P`: die Permutationsmatrix des Pivots ([`QRPivoted`](@ref) nur)

!!! Hinweis     Jeder Zugriff auf den oberen Dreifaktor über `F.R` allokiert ein neues Array. Es ist daher ratsam, dieses Array zu cachen, z.B. durch `R = F.R` und weiter mit `R` zu arbeiten.

Die Iteration der Zerlegung erzeugt die Komponenten `Q`, `R` und, falls vorhanden, `p`.

Die folgenden Funktionen sind für die `QR`-Objekte verfügbar: [`inv`](@ref), [`size`](@ref) und [`\`](@ref). Wenn `A` rechteckig ist, gibt `\` eine Lösung der kleinsten Quadrate zurück, und wenn die Lösung nicht eindeutig ist, wird die mit der kleinsten Norm zurückgegeben. Wenn `A` nicht vollen Rang hat, ist eine Zerlegung mit (Spalten-)Pivotierung erforderlich, um eine Lösung mit minimaler Norm zu erhalten.

Die Multiplikation in Bezug auf entweder volle/quadratische oder nicht volle/quadratische `Q` ist erlaubt, d.h. sowohl `F.Q*F.R` als auch `F.Q*A` werden unterstützt. Eine `Q`-Matrix kann mit [`Matrix`](@ref) in eine reguläre Matrix umgewandelt werden. Diese Operation gibt den "dünnen" Q-Faktor zurück, d.h., wenn `A` `m`×`n` mit `m>=n` ist, dann ergibt `Matrix(F.Q)` eine `m`×`n` Matrix mit orthonormalen Spalten. Um den "vollen" Q-Faktor, eine `m`×`m` orthogonale Matrix, abzurufen, verwenden Sie `F.Q*I` oder `collect(F.Q)`. Wenn `m<=n`, dann ergibt `Matrix(F.Q)` eine `m`×`m` orthogonale Matrix.

Die Blockgröße für die QR-Zerlegung kann durch das Schlüsselwort-Argument `blocksize :: Integer` angegeben werden, wenn `pivot == NoPivot()` und `A isa StridedMatrix{<:BlasFloat}`. Es wird ignoriert, wenn `blocksize > minimum(size(A))`. Siehe [`QRCompactWY`](@ref).

!!! Kompatibilität "Julia 1.4"     Das Schlüsselwort-Argument `blocksize` erfordert Julia 1.4 oder höher.

# Beispiele

```jldoctest
julia> A = [3.0 -6.0; 4.0 -8.0; 0.0 1.0]
3×2 Matrix{Float64}:
 3.0  -6.0
 4.0  -8.0
 0.0   1.0

julia> F = qr(A)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q-Faktor: 3×3 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R-Faktor:
2×2 Matrix{Float64}:
 -5.0  10.0
  0.0  -1.0

julia> F.Q * F.R == A
true
```

!!! Hinweis     `qr` gibt mehrere Typen zurück, da LAPACK mehrere Darstellungen verwendet, die die Speicheranforderungen für Produkte von Householder-Elementarreflektoren minimieren, sodass die `Q`- und `R`-Matrizen kompakt gespeichert werden können, anstatt als zwei separate dichte Matrizen.
