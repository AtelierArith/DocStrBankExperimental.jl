```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/LinearAlgebra/docs/src/index.md"
```

# [Linear Algebra](@id man-linalg)

```@meta
DocTestSetup = :(using LinearAlgebra)
```

Zusätzlich zu (und als Teil von) seiner Unterstützung für mehrdimensionale Arrays bietet Julia native Implementierungen vieler gängiger und nützlicher lineare Algebraoperationen, die mit `using LinearAlgebra` geladen werden können. Grundlegende Operationen wie [`tr`](@ref), [`det`](@ref) und [`inv`](@ref) werden alle unterstützt:

```jldoctest
julia> A = [1 2 3; 4 1 6; 7 8 1]
3×3 Matrix{Int64}:
 1  2  3
 4  1  6
 7  8  1

julia> tr(A)
3

julia> det(A)
104.0

julia> inv(A)
3×3 Matrix{Float64}:
 -0.451923   0.211538    0.0865385
  0.365385  -0.192308    0.0576923
  0.240385   0.0576923  -0.0673077
```

Neben anderen nützlichen Operationen, wie dem Finden von Eigenwerten oder Eigenvektoren:

```jldoctest
julia> A = [-4. -17.; 2. 2.]
2×2 Matrix{Float64}:
 -4.0  -17.0
  2.0    2.0

julia> eigvals(A)
2-element Vector{ComplexF64}:
 -1.0 - 5.0im
 -1.0 + 5.0im

julia> eigvecs(A)
2×2 Matrix{ComplexF64}:
  0.945905-0.0im        0.945905+0.0im
 -0.166924+0.278207im  -0.166924-0.278207im
```

Darüber hinaus bietet Julia viele [factorizations](@ref man-linalg-factorizations), die verwendet werden können, um Probleme wie lineare Lösungen oder Matrixexponentiation zu beschleunigen, indem eine Matrix in eine Form vorfaktorisiert wird, die für das Problem besser geeignet ist (aus Leistungs- oder Speichergründen). Siehe die Dokumentation zu [`factorize`](@ref) für weitere Informationen. Als Beispiel:

```jldoctest
julia> A = [1.5 2 -4; 3 -1 -6; -10 2.3 4]
3×3 Matrix{Float64}:
   1.5   2.0  -4.0
   3.0  -1.0  -6.0
 -10.0   2.3   4.0

julia> factorize(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
3×3 Matrix{Float64}:
  1.0    0.0       0.0
 -0.15   1.0       0.0
 -0.3   -0.132196  1.0
U factor:
3×3 Matrix{Float64}:
 -10.0  2.3     4.0
   0.0  2.345  -3.4
   0.0  0.0    -5.24947
```

Da `A` nicht hermitesch, symmetrisch, dreieckig, tridiagonal oder bidiagonal ist, könnte eine LU-Zerlegung das Beste sein, was wir tun können. Vergleiche mit:

```jldoctest
julia> B = [1.5 2 -4; 2 -1 -3; -4 -3 5]
3×3 Matrix{Float64}:
  1.5   2.0  -4.0
  2.0  -1.0  -3.0
 -4.0  -3.0   5.0

julia> factorize(B)
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D factor:
3×3 Tridiagonal{Float64, Vector{Float64}}:
 -1.64286   0.0   ⋅
  0.0      -2.8  0.0
   ⋅        0.0  5.0
U factor:
3×3 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.142857  -0.8
  ⋅   1.0       -0.6
  ⋅    ⋅         1.0
permutation:
3-element Vector{Int64}:
 1
 2
 3
```

Hier konnte Julia feststellen, dass `B` tatsächlich symmetrisch ist, und verwendete eine passendere Faktorisierung. Oft ist es möglich, effizienteren Code für eine Matrix zu schreiben, von der bekannt ist, dass sie bestimmte Eigenschaften hat, z. B. dass sie symmetrisch oder tridiagonal ist. Julia bietet einige spezielle Typen an, damit Sie Matrizen mit diesen Eigenschaften "taggen" können. Zum Beispiel:

```jldoctest
julia> B = [1.5 2 -4; 2 -1 -3; -4 -3 5]
3×3 Matrix{Float64}:
  1.5   2.0  -4.0
  2.0  -1.0  -3.0
 -4.0  -3.0   5.0

julia> sB = Symmetric(B)
3×3 Symmetric{Float64, Matrix{Float64}}:
  1.5   2.0  -4.0
  2.0  -1.0  -3.0
 -4.0  -3.0   5.0
```

`sB` wurde als eine (reelle) symmetrische Matrix gekennzeichnet, sodass für spätere Operationen, die wir an ihr durchführen könnten, wie Eigenfaktorisierung oder Berechnung von Matrix-Vektor-Produkten, Effizienzen gefunden werden können, indem wir nur auf die Hälfte davon verweisen. Zum Beispiel:

```jldoctest
julia> B = [1.5 2 -4; 2 -1 -3; -4 -3 5]
3×3 Matrix{Float64}:
  1.5   2.0  -4.0
  2.0  -1.0  -3.0
 -4.0  -3.0   5.0

julia> sB = Symmetric(B)
3×3 Symmetric{Float64, Matrix{Float64}}:
  1.5   2.0  -4.0
  2.0  -1.0  -3.0
 -4.0  -3.0   5.0

julia> x = [1; 2; 3]
3-element Vector{Int64}:
 1
 2
 3

julia> sB\x
3-element Vector{Float64}:
 -1.7391304347826084
 -1.1086956521739126
 -1.4565217391304346
```

Der `\`-Operator führt hier die lineare Lösung durch. Der Links-Teilungsoperator ist ziemlich leistungsfähig und es ist einfach, kompakte, lesbare Codes zu schreiben, die flexibel genug sind, um alle Arten von Systemen linearer Gleichungen zu lösen.

## Special matrices

[Matrices with special symmetries and structures](https://www2.imm.dtu.dk/pubdb/views/publication_details.php?id=3274) treten häufig in der linearen Algebra auf und sind oft mit verschiedenen Matrixfaktorisierungen verbunden. Julia bietet eine reiche Sammlung spezieller Matrizenarten, die eine schnelle Berechnung mit spezialisierten Routinen ermöglichen, die speziell für bestimmte Matrizenarten entwickelt wurden.

Die folgenden Tabellen fassen die Arten von speziellen Matrizen zusammen, die in Julia implementiert wurden, sowie ob Hooks zu verschiedenen optimierten Methoden für sie in LAPACK verfügbar sind.

| Type                          | Description                                                                                   |
|:----------------------------- |:--------------------------------------------------------------------------------------------- |
| [`Symmetric`](@ref)           | [Symmetric matrix](https://en.wikipedia.org/wiki/Symmetric_matrix)                            |
| [`Hermitian`](@ref)           | [Hermitian matrix](https://en.wikipedia.org/wiki/Hermitian_matrix)                            |
| [`UpperTriangular`](@ref)     | Upper [triangular matrix](https://en.wikipedia.org/wiki/Triangular_matrix)                    |
| [`UnitUpperTriangular`](@ref) | Upper [triangular matrix](https://en.wikipedia.org/wiki/Triangular_matrix) with unit diagonal |
| [`LowerTriangular`](@ref)     | Lower [triangular matrix](https://en.wikipedia.org/wiki/Triangular_matrix)                    |
| [`UnitLowerTriangular`](@ref) | Lower [triangular matrix](https://en.wikipedia.org/wiki/Triangular_matrix) with unit diagonal |
| [`UpperHessenberg`](@ref)     | Upper [Hessenberg matrix](https://en.wikipedia.org/wiki/Hessenberg_matrix)                    |
| [`Tridiagonal`](@ref)         | [Tridiagonal matrix](https://en.wikipedia.org/wiki/Tridiagonal_matrix)                        |
| [`SymTridiagonal`](@ref)      | Symmetric tridiagonal matrix                                                                  |
| [`Bidiagonal`](@ref)          | Upper/lower [bidiagonal matrix](https://en.wikipedia.org/wiki/Bidiagonal_matrix)              |
| [`Diagonal`](@ref)            | [Diagonal matrix](https://en.wikipedia.org/wiki/Diagonal_matrix)                              |
| [`UniformScaling`](@ref)      | [Uniform scaling operator](https://en.wikipedia.org/wiki/Uniform_scaling)                     |

### Elementary operations

| Matrix type                   | `+` | `-` | `*` | `\` | Other functions with optimized methods                       |
|:----------------------------- |:--- |:--- |:--- |:--- |:------------------------------------------------------------ |
| [`Symmetric`](@ref)           |     |     |     | MV  | [`inv`](@ref), [`sqrt`](@ref), [`cbrt`](@ref), [`exp`](@ref) |
| [`Hermitian`](@ref)           |     |     |     | MV  | [`inv`](@ref), [`sqrt`](@ref), [`cbrt`](@ref), [`exp`](@ref) |
| [`UpperTriangular`](@ref)     |     |     | MV  | MV  | [`inv`](@ref), [`det`](@ref), [`logdet`](@ref)               |
| [`UnitUpperTriangular`](@ref) |     |     | MV  | MV  | [`inv`](@ref), [`det`](@ref), [`logdet`](@ref)               |
| [`LowerTriangular`](@ref)     |     |     | MV  | MV  | [`inv`](@ref), [`det`](@ref), [`logdet`](@ref)               |
| [`UnitLowerTriangular`](@ref) |     |     | MV  | MV  | [`inv`](@ref), [`det`](@ref), [`logdet`](@ref)               |
| [`UpperHessenberg`](@ref)     |     |     |     | MM  | [`inv`](@ref), [`det`](@ref)                                 |
| [`SymTridiagonal`](@ref)      | M   | M   | MS  | MV  | [`eigmax`](@ref), [`eigmin`](@ref)                           |
| [`Tridiagonal`](@ref)         | M   | M   | MS  | MV  |                                                              |
| [`Bidiagonal`](@ref)          | M   | M   | MS  | MV  |                                                              |
| [`Diagonal`](@ref)            | M   | M   | MV  | MV  | [`inv`](@ref), [`det`](@ref), [`logdet`](@ref), [`/`](@ref)  |
| [`UniformScaling`](@ref)      | M   | M   | MVS | MVS | [`/`](@ref)                                                  |

Legende:

| Key        | Description                                                   |
|:---------- |:------------------------------------------------------------- |
| M (matrix) | An optimized method for matrix-matrix operations is available |
| V (vector) | An optimized method for matrix-vector operations is available |
| S (scalar) | An optimized method for matrix-scalar operations is available |

### Matrix factorizations

| Matrix type                   | LAPACK | [`eigen`](@ref) | [`eigvals`](@ref) | [`eigvecs`](@ref) | [`svd`](@ref) | [`svdvals`](@ref) |
|:----------------------------- |:------ |:--------------- |:----------------- |:----------------- |:------------- |:----------------- |
| [`Symmetric`](@ref)           | SY     |                 | ARI               |                   |               |                   |
| [`Hermitian`](@ref)           | HE     |                 | ARI               |                   |               |                   |
| [`UpperTriangular`](@ref)     | TR     | A               | A                 | A                 |               |                   |
| [`UnitUpperTriangular`](@ref) | TR     | A               | A                 | A                 |               |                   |
| [`LowerTriangular`](@ref)     | TR     | A               | A                 | A                 |               |                   |
| [`UnitLowerTriangular`](@ref) | TR     | A               | A                 | A                 |               |                   |
| [`SymTridiagonal`](@ref)      | ST     | A               | ARI               | AV                |               |                   |
| [`Tridiagonal`](@ref)         | GT     |                 |                   |                   |               |                   |
| [`Bidiagonal`](@ref)          | BD     |                 |                   |                   | A             | A                 |
| [`Diagonal`](@ref)            | DI     |                 | A                 |                   |               |                   |

Legende:

| Key          | Description                                                                                                                     | Example              |
|:------------ |:------------------------------------------------------------------------------------------------------------------------------- |:-------------------- |
| A (all)      | An optimized method to find all the characteristic values and/or vectors is available                                           | e.g. `eigvals(M)`    |
| R (range)    | An optimized method to find the `il`th through the `ih`th characteristic values are available                                   | `eigvals(M, il, ih)` |
| I (interval) | An optimized method to find the characteristic values in the interval [`vl`, `vh`] is available                                 | `eigvals(M, vl, vh)` |
| V (vectors)  | An optimized method to find the characteristic vectors corresponding to the characteristic values `x=[x1, x2,...]` is available | `eigvecs(M, x)`      |

### The uniform scaling operator

Ein [`UniformScaling`](@ref) Operator repräsentiert einen Skalar mal den Identitätsoperator, `λ*I`. Der Identitätsoperator `I` ist als Konstante definiert und ist eine Instanz von `UniformScaling`. Die Größe dieser Operatoren ist generisch und entspricht der anderen Matrix in den binären Operationen [`+`](@ref), [`-`](@ref), [`*`](@ref) und [`\`](@ref). Für `A+I` und `A-I` bedeutet dies, dass `A` quadratisch sein muss. Die Multiplikation mit dem Identitätsoperator `I` ist ein Noop (außer zur Überprüfung, dass der Skalierungsfaktor eins ist) und daher nahezu ohne Overhead.

Um den `UniformScaling`-Operator in Aktion zu sehen:

```jldoctest
julia> U = UniformScaling(2);

julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> a + U
2×2 Matrix{Int64}:
 3  2
 3  6

julia> a * U
2×2 Matrix{Int64}:
 2  4
 6  8

julia> [a U]
2×4 Matrix{Int64}:
 1  2  2  0
 3  4  0  2

julia> b = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> b - U
ERROR: DimensionMismatch: matrix is not square: dimensions are (2, 3)
Stacktrace:
[...]
```

Wenn Sie viele Systeme der Form `(A+μI)x = b` für dasselbe `A` und unterschiedliche `μ` lösen müssen, kann es vorteilhaft sein, zuerst die Hessenberg-Faktorisierung `F` von `A` über die [`hessenberg`](@ref)-Funktion zu berechnen. Mit `F` verwendet Julia einen effizienten Algorithmus für `(F+μ*I) \ b` (äquivalent zu `(A+μ*I)x \ b`) und verwandte Operationen wie Determinanten.

## [Matrix factorizations](@id man-linalg-factorizations)

[Matrix factorizations (a.k.a. matrix decompositions)](https://en.wikipedia.org/wiki/Matrix_decomposition) berechnet die Faktorisierung einer Matrix in ein Produkt von Matrizen und ist eines der zentralen Konzepte in der (numerischen) linearen Algebra.

Die folgende Tabelle fasst die Arten von Matrixfaktorisierungen zusammen, die in Julia implementiert wurden. Einzelheiten zu den zugehörigen Methoden finden Sie im Abschnitt [Standard functions](@ref) der Dokumentation zur linearen Algebra.

| Type               | Description                                                                                                                       |
|:------------------ |:--------------------------------------------------------------------------------------------------------------------------------- |
| `BunchKaufman`     | Bunch-Kaufman factorization                                                                                                       |
| `Cholesky`         | [Cholesky factorization](https://en.wikipedia.org/wiki/Cholesky_decomposition)                                                    |
| `CholeskyPivoted`  | [Pivoted](https://en.wikipedia.org/wiki/Pivot_element) Cholesky factorization                                                     |
| `LDLt`             | [LDL(T) factorization](https://en.wikipedia.org/wiki/Cholesky_decomposition#LDL_decomposition)                                    |
| `LU`               | [LU factorization](https://en.wikipedia.org/wiki/LU_decomposition)                                                                |
| `QR`               | [QR factorization](https://en.wikipedia.org/wiki/QR_decomposition)                                                                |
| `QRCompactWY`      | Compact WY form of the QR factorization                                                                                           |
| `QRPivoted`        | Pivoted [QR factorization](https://en.wikipedia.org/wiki/QR_decomposition)                                                        |
| `LQ`               | [QR factorization](https://en.wikipedia.org/wiki/QR_decomposition) of `transpose(A)`                                              |
| `Hessenberg`       | [Hessenberg decomposition](https://mathworld.wolfram.com/HessenbergDecomposition.html)                                            |
| `Eigen`            | [Spectral decomposition](https://en.wikipedia.org/wiki/Eigendecomposition_of_a_matrix)                                            |
| `GeneralizedEigen` | [Generalized spectral decomposition](https://en.wikipedia.org/wiki/Eigendecomposition_of_a_matrix#Generalized_eigenvalue_problem) |
| `SVD`              | [Singular value decomposition](https://en.wikipedia.org/wiki/Singular_value_decomposition)                                        |
| `GeneralizedSVD`   | [Generalized SVD](https://en.wikipedia.org/wiki/Generalized_singular_value_decomposition#Higher_order_version)                    |
| `Schur`            | [Schur decomposition](https://en.wikipedia.org/wiki/Schur_decomposition)                                                          |
| `GeneralizedSchur` | [Generalized Schur decomposition](https://en.wikipedia.org/wiki/Schur_decomposition#Generalized_Schur_decomposition)              |

Adjunkte und Transponierte von [`Factorization`](@ref) Objekten sind faul in `AdjointFactorization` und `TransposeFactorization` Objekten eingewickelt. Generell werden Transponierte von reellen `Factorization`s als `AdjointFactorization` eingewickelt.

## [Orthogonal matrices (`AbstractQ`)](@id man-linalg-abstractq)

Einige Matrixfaktorisierungen erzeugen orthogonale/einheitliche "Matrix"-Faktoren. Diese Faktorisierungen umfassen QR-bezogene Faktorisierungen, die aus Aufrufen von [`qr`](@ref) erhalten werden, d.h. `QR`, `QRCompactWY` und `QRPivoted`, die Hessenberg-Faktorisierung, die aus Aufrufen von [`hessenberg`](@ref) erhalten wird, und die LQ-Faktorisierung, die aus [`lq`](@ref) erhalten wird. Während diese orthogonalen/einheitlichen Faktoren eine Matrixdarstellung zulassen, ist ihre interne Darstellung aus Leistungs- und Speichergründen unterschiedlich. Daher sollten sie eher als matrixgestützte, funktionsbasierte lineare Operatoren betrachtet werden. Insbesondere erfordert das Lesen beispielsweise einer Spalte ihrer Matrixdarstellung das Ausführen von "Matrix"-Vektor-Multiplikationscode, anstatt einfach Daten aus dem Speicher zu lesen (möglicherweise Teile des Vektors mit strukturellen Nullen zu füllen). Ein weiterer klarer Unterschied zu anderen, nicht-triangularen Matrizenarten besteht darin, dass der zugrunde liegende Multiplikationscode eine In-Place-Modifikation während der Multiplikation ermöglicht. Darüber hinaus können Objekte spezifischer `AbstractQ`-Subtypen, wie sie über `4d61726b646f776e2e436f64652822222c202271722229_40726566`, `4d61726b646f776e2e436f64652822222c202268657373656e626572672229_40726566` und `4d61726b646f776e2e436f64652822222c20226c712229_40726566` erstellt werden, je nach Kontext wie eine quadratische oder rechteckige Matrix verhalten:

```julia
julia> using LinearAlgebra

julia> Q = qr(rand(3,2)).Q
3×3 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}

julia> Matrix(Q)
3×2 Matrix{Float64}:
 -0.320597   0.865734
 -0.765834  -0.475694
 -0.557419   0.155628

julia> Q*I
3×3 Matrix{Float64}:
 -0.320597   0.865734  -0.384346
 -0.765834  -0.475694  -0.432683
 -0.557419   0.155628   0.815514

julia> Q*ones(2)
3-element Vector{Float64}:
  0.5451367118802273
 -1.241527373086654
 -0.40179067589600226

julia> Q*ones(3)
3-element Vector{Float64}:
  0.16079054743832022
 -1.674209978965636
  0.41372375588835797

julia> ones(1,2) * Q'
1×3 Matrix{Float64}:
 0.545137  -1.24153  -0.401791

julia> ones(1,3) * Q'
1×3 Matrix{Float64}:
 0.160791  -1.67421  0.413724
```

Aufgrund dieser Unterscheidung von dichten oder strukturierten Matrizen unterliegt der abstrakte `AbstractQ`-Typ nicht dem `AbstractMatrix`, sondern hat stattdessen seine eigene Typ-Hierarchie. Benutzerdefinierte Typen, die von `AbstractQ` abgeleitet sind, können auf generische Rückfalle zurückgreifen, wenn die folgende Schnittstelle erfüllt ist. Zum Beispiel für

```julia
struct MyQ{T} <: LinearAlgebra.AbstractQ{T}
    # required fields
end
```

Überladungen bereitstellen für

```julia
Base.size(Q::MyQ) # size of corresponding square matrix representation
Base.convert(::Type{AbstractQ{T}}, Q::MyQ) # eltype promotion [optional]
LinearAlgebra.lmul!(Q::MyQ, x::AbstractVecOrMat) # left-multiplication
LinearAlgebra.rmul!(A::AbstractMatrix, Q::MyQ) # right-multiplication
```

Wenn die `eltype`-Promotion nicht von Interesse ist, ist die `convert`-Methode nicht erforderlich, da `convert(::Type{AbstractQ{T}}, Q::AbstractQ{T})` standardmäßig `Q` selbst zurückgibt. Adjunkte von Objekten des Typs `AbstractQ` werden faul in einem `AdjointQ`-Wrapper-Typ verpackt, der seine eigenen `LinearAlgebra.lmul!`- und `LinearAlgebra.rmul!`-Methoden benötigt. Mit diesem Satz von Methoden kann jede `Q::MyQ` wie eine Matrix verwendet werden, vorzugsweise in einem multiplikativen Kontext: Multiplikation über `*` mit Skalaren, Vektoren und Matrizen von links und rechts, das Erhalten einer Matrixdarstellung von `Q` über `Matrix(Q)` (oder `Q*I`) und das Indizieren in die Matrixdarstellung funktionieren alle. Im Gegensatz dazu schlagen Addition und Subtraktion sowie allgemeiner das Broadcasting über Elemente in der Matrixdarstellung fehl, da dies sehr ineffizient wäre. Für solche Anwendungsfälle sollten Sie in Betracht ziehen, die Matrixdarstellung im Voraus zu berechnen und sie für die zukünftige Wiederverwendung zu cachen.

## [Pivoting Strategies](@id man-linalg-pivoting-strategies)

Mehrere von Julias [matrix factorizations](@ref man-linalg-factorizations) unterstützen [pivoting](https://en.wikipedia.org/wiki/Pivot_element), was verwendet werden kann, um ihre numerische Stabilität zu verbessern. Tatsächlich können einige Matrixfaktorisierungen, wie die LU-Faktorisierung, ohne Pivotierung fehlschlagen.

In pivoting, first, a [pivot element](https://en.wikipedia.org/wiki/Pivot_element) with good numerical properties is chosen based on a pivoting strategy. Next, the rows and columns of the original matrix are permuted to bring the chosen element in place for subsequent computation. Furthermore, the process is repeated for each stage of the factorization.

Folglich umfassen neben den herkömmlichen Matrixfaktoren die Ausgaben von pivotierten Faktorisierungsschemata auch Permutationsmatrizen.

In the following, the pivoting strategies implemented in Julia are briefly described. Note that not all matrix factorizations may support them. Consult the documentation of the respective [matrix factorization](@ref man-linalg-factorizations) for details on the supported pivoting strategies.

Siehe auch [`LinearAlgebra.ZeroPivotException`](@ref).

```@docs
LinearAlgebra.NoPivot
LinearAlgebra.RowNonZero
LinearAlgebra.RowMaximum
LinearAlgebra.ColumnNorm
```

## Standard functions

Lineare Algebra-Funktionen in Julia werden größtenteils durch den Aufruf von Funktionen aus [LAPACK](https://www.netlib.org/lapack/) implementiert. Sparse-Matrix-Faktorisierungen rufen Funktionen aus [SuiteSparse](http://suitesparse.com) auf. Andere spärliche Solver sind als Julia-Pakete verfügbar.

```@docs
Base.:*(::AbstractMatrix, ::AbstractMatrix)
Base.:*(::AbstractMatrix, ::AbstractMatrix, ::AbstractVector)
Base.:\(::AbstractMatrix, ::AbstractVecOrMat)
Base.:/(::AbstractVecOrMat, ::AbstractVecOrMat)
LinearAlgebra.SingularException
LinearAlgebra.PosDefException
LinearAlgebra.ZeroPivotException
LinearAlgebra.RankDeficientException
LinearAlgebra.LAPACKException
LinearAlgebra.dot
LinearAlgebra.dot(::Any, ::Any, ::Any)
LinearAlgebra.cross
LinearAlgebra.axpy!
LinearAlgebra.axpby!
LinearAlgebra.rotate!
LinearAlgebra.reflect!
LinearAlgebra.factorize
LinearAlgebra.Diagonal
LinearAlgebra.Bidiagonal
LinearAlgebra.SymTridiagonal
LinearAlgebra.Tridiagonal
LinearAlgebra.Symmetric
LinearAlgebra.Hermitian
LinearAlgebra.LowerTriangular
LinearAlgebra.UpperTriangular
LinearAlgebra.UnitLowerTriangular
LinearAlgebra.UnitUpperTriangular
LinearAlgebra.UpperHessenberg
LinearAlgebra.UniformScaling
LinearAlgebra.I
LinearAlgebra.UniformScaling(::Integer)
LinearAlgebra.Factorization
LinearAlgebra.LU
LinearAlgebra.lu
LinearAlgebra.lu!
LinearAlgebra.Cholesky
LinearAlgebra.CholeskyPivoted
LinearAlgebra.cholesky
LinearAlgebra.cholesky!
LinearAlgebra.lowrankupdate
LinearAlgebra.lowrankdowndate
LinearAlgebra.lowrankupdate!
LinearAlgebra.lowrankdowndate!
LinearAlgebra.LDLt
LinearAlgebra.ldlt
LinearAlgebra.ldlt!
LinearAlgebra.QR
LinearAlgebra.QRCompactWY
LinearAlgebra.QRPivoted
LinearAlgebra.qr
LinearAlgebra.qr!
LinearAlgebra.LQ
LinearAlgebra.lq
LinearAlgebra.lq!
LinearAlgebra.BunchKaufman
LinearAlgebra.bunchkaufman
LinearAlgebra.bunchkaufman!
LinearAlgebra.Eigen
LinearAlgebra.GeneralizedEigen
LinearAlgebra.eigvals
LinearAlgebra.eigvals!
LinearAlgebra.eigmax
LinearAlgebra.eigmin
LinearAlgebra.eigvecs
LinearAlgebra.eigen
LinearAlgebra.eigen!
LinearAlgebra.Hessenberg
LinearAlgebra.hessenberg
LinearAlgebra.hessenberg!
LinearAlgebra.Schur
LinearAlgebra.GeneralizedSchur
LinearAlgebra.schur
LinearAlgebra.schur!
LinearAlgebra.ordschur
LinearAlgebra.ordschur!
LinearAlgebra.SVD
LinearAlgebra.GeneralizedSVD
LinearAlgebra.svd
LinearAlgebra.svd!
LinearAlgebra.svdvals
LinearAlgebra.svdvals!
LinearAlgebra.Givens
LinearAlgebra.givens
LinearAlgebra.triu
LinearAlgebra.triu!
LinearAlgebra.tril
LinearAlgebra.tril!
LinearAlgebra.diagind
LinearAlgebra.diag
LinearAlgebra.diagm
LinearAlgebra.rank
LinearAlgebra.norm
LinearAlgebra.opnorm
LinearAlgebra.normalize!
LinearAlgebra.normalize
LinearAlgebra.cond
LinearAlgebra.condskeel
LinearAlgebra.tr
LinearAlgebra.det
LinearAlgebra.logdet
LinearAlgebra.logabsdet
Base.inv(::AbstractMatrix)
LinearAlgebra.pinv
LinearAlgebra.nullspace
Base.kron
Base.kron!
LinearAlgebra.exp(::StridedMatrix{<:LinearAlgebra.BlasFloat})
Base.cis(::AbstractMatrix)
Base.:^(::AbstractMatrix, ::Number)
Base.:^(::Number, ::AbstractMatrix)
LinearAlgebra.log(::StridedMatrix)
LinearAlgebra.sqrt(::StridedMatrix)
LinearAlgebra.cbrt(::AbstractMatrix{<:Real})
LinearAlgebra.cos(::StridedMatrix{<:Real})
LinearAlgebra.sin(::StridedMatrix{<:Real})
LinearAlgebra.sincos(::StridedMatrix{<:Real})
LinearAlgebra.tan(::StridedMatrix{<:Real})
LinearAlgebra.sec(::StridedMatrix)
LinearAlgebra.csc(::StridedMatrix)
LinearAlgebra.cot(::StridedMatrix)
LinearAlgebra.cosh(::StridedMatrix)
LinearAlgebra.sinh(::StridedMatrix)
LinearAlgebra.tanh(::StridedMatrix)
LinearAlgebra.sech(::StridedMatrix)
LinearAlgebra.csch(::StridedMatrix)
LinearAlgebra.coth(::StridedMatrix)
LinearAlgebra.acos(::StridedMatrix)
LinearAlgebra.asin(::StridedMatrix)
LinearAlgebra.atan(::StridedMatrix)
LinearAlgebra.asec(::StridedMatrix)
LinearAlgebra.acsc(::StridedMatrix)
LinearAlgebra.acot(::StridedMatrix)
LinearAlgebra.acosh(::StridedMatrix)
LinearAlgebra.asinh(::StridedMatrix)
LinearAlgebra.atanh(::StridedMatrix)
LinearAlgebra.asech(::StridedMatrix)
LinearAlgebra.acsch(::StridedMatrix)
LinearAlgebra.acoth(::StridedMatrix)
LinearAlgebra.lyap
LinearAlgebra.sylvester
LinearAlgebra.issuccess
LinearAlgebra.issymmetric
LinearAlgebra.isposdef
LinearAlgebra.isposdef!
LinearAlgebra.istril
LinearAlgebra.istriu
LinearAlgebra.isdiag
LinearAlgebra.ishermitian
Base.transpose
LinearAlgebra.transpose!
LinearAlgebra.Transpose
LinearAlgebra.TransposeFactorization
Base.adjoint
LinearAlgebra.adjoint!
LinearAlgebra.Adjoint
LinearAlgebra.AdjointFactorization
Base.copy(::Union{Transpose,Adjoint})
LinearAlgebra.stride1
LinearAlgebra.checksquare
LinearAlgebra.peakflops
LinearAlgebra.hermitianpart
LinearAlgebra.hermitianpart!
LinearAlgebra.copy_adjoint!
LinearAlgebra.copy_transpose!
```

## Low-level matrix operations

In vielen Fällen gibt es In-Place-Versionen von Matrixoperationen, die es Ihnen ermöglichen, einen vorab zugewiesenen Ausgabvektor oder eine Ausgabematrix bereitzustellen. Dies ist nützlich, wenn Sie kritischen Code optimieren möchten, um die Überheadkosten wiederholter Zuweisungen zu vermeiden. Diese In-Place-Operationen sind unten mit `!` (z. B. `mul!`) gemäß der üblichen Julia-Konvention versehen.

```@docs
LinearAlgebra.mul!
LinearAlgebra.lmul!
LinearAlgebra.rmul!
LinearAlgebra.ldiv!
LinearAlgebra.rdiv!
```

## BLAS functions

In Julia (wie in vielen wissenschaftlichen Berechnungen) basieren dichte lineare Algebraoperationen auf der [LAPACK library](https://www.netlib.org/lapack/), die wiederum auf grundlegenden linearen Algebra-Bausteinen basiert, die als [BLAS](https://www.netlib.org/blas/) bekannt sind. Es gibt hochoptimierte Implementierungen von BLAS, die für jede Computerarchitektur verfügbar sind, und manchmal ist es in Hochleistungs-Linear-Algebra-Routinen nützlich, die BLAS-Funktionen direkt aufzurufen.

`LinearAlgebra.BLAS` bietet Wrapper für einige der BLAS-Funktionen. Die BLAS-Funktionen, die eines der Eingabearrays überschreiben, haben Namen, die mit `'!'` enden. In der Regel hat eine BLAS-Funktion vier Methoden definiert, für [`Float32`](@ref), [`Float64`](@ref), [`ComplexF32`](@ref Complex) und [`ComplexF64`](@ref Complex) Arrays.

### [BLAS character arguments](@id stdlib-blas-chars)

Viele BLAS-Funktionen akzeptieren Argumente, die bestimmen, ob ein Argument transponiert werden soll (`trans`), welches Dreieck einer Matrix referenziert werden soll (`uplo` oder `ul`), ob die Diagonale einer dreieckigen Matrix als ganz eins angenommen werden kann (`dA`) oder auf welcher Seite einer Matrixmultiplikation das Eingabeargument gehört (`side`). Die Möglichkeiten sind:

#### [Multiplication order](@id stdlib-blas-side)

| `side` | Meaning                                                             |
|:------ |:------------------------------------------------------------------- |
| `'L'`  | The argument goes on the *left* side of a matrix-matrix operation.  |
| `'R'`  | The argument goes on the *right* side of a matrix-matrix operation. |

#### [Triangle referencing](@id stdlib-blas-uplo)

| `uplo`/`ul` | Meaning                                               |
|:----------- |:----------------------------------------------------- |
| `'U'`       | Only the *upper* triangle of the matrix will be used. |
| `'L'`       | Only the *lower* triangle of the matrix will be used. |

#### [Transposition operation](@id stdlib-blas-trans)

| `trans`/`tX` | Meaning                                                 |
|:------------ |:------------------------------------------------------- |
| `'N'`        | The input matrix `X` is not transposed or conjugated.   |
| `'T'`        | The input matrix `X` will be transposed.                |
| `'C'`        | The input matrix `X` will be conjugated and transposed. |

#### [Unit diagonal](@id stdlib-blas-diag)

| `diag`/`dX` | Meaning                                                   |
|:----------- |:--------------------------------------------------------- |
| `'N'`       | The diagonal values of the matrix `X` will be read.       |
| `'U'`       | The diagonal of the matrix `X` is assumed to be all ones. |

```@docs
LinearAlgebra.BLAS
LinearAlgebra.BLAS.set_num_threads
LinearAlgebra.BLAS.get_num_threads
```

BLAS-Funktionen können in drei Gruppen unterteilt werden, die auch als drei Ebenen bezeichnet werden, abhängig davon, wann sie erstmals vorgeschlagen wurden, welche Art von Eingabeparametern verwendet wird und wie komplex die Operation ist.

### Level 1 BLAS functions

Die Level-1-BLAS-Funktionen wurden erstmals in [(Lawson, 1979)][Lawson-1979] vorgeschlagen und definieren Operationen zwischen Skalaren und Vektoren.

[Lawson-1979]: https://dl.acm.org/doi/10.1145/355841.355847

```@docs
# xROTG
# xROTMG
LinearAlgebra.BLAS.rot!
# xROTM
# xSWAP
LinearAlgebra.BLAS.scal!
LinearAlgebra.BLAS.scal
LinearAlgebra.BLAS.blascopy!
# xAXPY!
# xAXPBY!
LinearAlgebra.BLAS.dot
LinearAlgebra.BLAS.dotu
LinearAlgebra.BLAS.dotc
# xxDOT
LinearAlgebra.BLAS.nrm2
LinearAlgebra.BLAS.asum
LinearAlgebra.BLAS.iamax
```

### Level 2 BLAS functions

Die Level-2-BLAS-Funktionen wurden in [(Dongarra, 1988)][Dongarra-1988] veröffentlicht und definieren Matrix-Vektor-Operationen.

[Dongarra-1988]: https://dl.acm.org/doi/10.1145/42288.42291

**Geben Sie einen Vektor zurück**

```@docs
LinearAlgebra.BLAS.gemv!
LinearAlgebra.BLAS.gemv(::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.gemv(::Any, ::Any, ::Any)
LinearAlgebra.BLAS.gbmv!
LinearAlgebra.BLAS.gbmv
LinearAlgebra.BLAS.hemv!
LinearAlgebra.BLAS.hemv(::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.hemv(::Any, ::Any, ::Any)
# hbmv!, hbmv
LinearAlgebra.BLAS.hpmv!
LinearAlgebra.BLAS.symv!
LinearAlgebra.BLAS.symv(::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.symv(::Any, ::Any, ::Any)
LinearAlgebra.BLAS.sbmv!
LinearAlgebra.BLAS.sbmv(::Any, ::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.sbmv(::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.spmv!
LinearAlgebra.BLAS.trmv!
LinearAlgebra.BLAS.trmv
# xTBMV
# xTPMV
LinearAlgebra.BLAS.trsv!
LinearAlgebra.BLAS.trsv
# xTBSV
# xTPSV
```

**eine Matrix zurückgeben**

```@docs
LinearAlgebra.BLAS.ger!
# xGERU
# xGERC
LinearAlgebra.BLAS.her!
# xHPR
# xHER2
# xHPR2
LinearAlgebra.BLAS.syr!
LinearAlgebra.BLAS.spr!
# xSYR2
# xSPR2
```

### Level 3 BLAS functions

Die Level-3-BLAS-Funktionen wurden in [(Dongarra, 1990)][Dongarra-1990] veröffentlicht und definieren Matrix-Matrix-Operationen.

[Dongarra-1990]: https://dl.acm.org/doi/10.1145/77626.79170

```@docs
LinearAlgebra.BLAS.gemmt!
LinearAlgebra.BLAS.gemmt(::Any, ::Any, ::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.gemmt(::Any, ::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.gemm!
LinearAlgebra.BLAS.gemm(::Any, ::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.gemm(::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.symm!
LinearAlgebra.BLAS.symm(::Any, ::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.symm(::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.hemm!
LinearAlgebra.BLAS.hemm(::Any, ::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.hemm(::Any, ::Any, ::Any, ::Any)
LinearAlgebra.BLAS.syrk!
LinearAlgebra.BLAS.syrk
LinearAlgebra.BLAS.herk!
LinearAlgebra.BLAS.herk
LinearAlgebra.BLAS.syr2k!
LinearAlgebra.BLAS.syr2k
LinearAlgebra.BLAS.her2k!
LinearAlgebra.BLAS.her2k
LinearAlgebra.BLAS.trmm!
LinearAlgebra.BLAS.trmm
LinearAlgebra.BLAS.trsm!
LinearAlgebra.BLAS.trsm
```

## [LAPACK functions](@id man-linalg-lapack-functions)

`LinearAlgebra.LAPACK` bietet Wrapper für einige der LAPACK-Funktionen der linearen Algebra. Die Funktionen, die eines der Eingabearrays überschreiben, haben Namen, die mit `'!'` enden.

In der Regel hat eine Funktion 4 Methoden definiert, eine für [`Float64`](@ref), [`Float32`](@ref), `ComplexF64` und `ComplexF32` Arrays.

Beachten Sie, dass die von Julia bereitgestellte LAPACK-API sich in Zukunft ändern kann und wird. Da diese API nicht benutzerorientiert ist, gibt es kein Engagement, diese spezifische Funktionalität in zukünftigen Versionen zu unterstützen oder abzulehnen.

```@docs
LinearAlgebra.LAPACK
LinearAlgebra.LAPACK.gbtrf!
LinearAlgebra.LAPACK.gbtrs!
LinearAlgebra.LAPACK.gebal!
LinearAlgebra.LAPACK.gebak!
LinearAlgebra.LAPACK.gebrd!
LinearAlgebra.LAPACK.gelqf!
LinearAlgebra.LAPACK.geqlf!
LinearAlgebra.LAPACK.geqrf!
LinearAlgebra.LAPACK.geqp3!
LinearAlgebra.LAPACK.gerqf!
LinearAlgebra.LAPACK.geqrt!
LinearAlgebra.LAPACK.geqrt3!
LinearAlgebra.LAPACK.getrf!
LinearAlgebra.LAPACK.tzrzf!
LinearAlgebra.LAPACK.ormrz!
LinearAlgebra.LAPACK.gels!
LinearAlgebra.LAPACK.gesv!
LinearAlgebra.LAPACK.getrs!
LinearAlgebra.LAPACK.getri!
LinearAlgebra.LAPACK.gesvx!
LinearAlgebra.LAPACK.gelsd!
LinearAlgebra.LAPACK.gelsy!
LinearAlgebra.LAPACK.gglse!
LinearAlgebra.LAPACK.geev!
LinearAlgebra.LAPACK.gesdd!
LinearAlgebra.LAPACK.gesvd!
LinearAlgebra.LAPACK.ggsvd!
LinearAlgebra.LAPACK.ggsvd3!
LinearAlgebra.LAPACK.geevx!
LinearAlgebra.LAPACK.ggev!
LinearAlgebra.LAPACK.ggev3!
LinearAlgebra.LAPACK.gtsv!
LinearAlgebra.LAPACK.gttrf!
LinearAlgebra.LAPACK.gttrs!
LinearAlgebra.LAPACK.orglq!
LinearAlgebra.LAPACK.orgqr!
LinearAlgebra.LAPACK.orgql!
LinearAlgebra.LAPACK.orgrq!
LinearAlgebra.LAPACK.ormlq!
LinearAlgebra.LAPACK.ormqr!
LinearAlgebra.LAPACK.ormql!
LinearAlgebra.LAPACK.ormrq!
LinearAlgebra.LAPACK.gemqrt!
LinearAlgebra.LAPACK.posv!
LinearAlgebra.LAPACK.potrf!
LinearAlgebra.LAPACK.potri!
LinearAlgebra.LAPACK.potrs!
LinearAlgebra.LAPACK.pstrf!
LinearAlgebra.LAPACK.ptsv!
LinearAlgebra.LAPACK.pttrf!
LinearAlgebra.LAPACK.pttrs!
LinearAlgebra.LAPACK.trtri!
LinearAlgebra.LAPACK.trtrs!
LinearAlgebra.LAPACK.trcon!
LinearAlgebra.LAPACK.trevc!
LinearAlgebra.LAPACK.trrfs!
LinearAlgebra.LAPACK.stev!
LinearAlgebra.LAPACK.stebz!
LinearAlgebra.LAPACK.stegr!
LinearAlgebra.LAPACK.stein!
LinearAlgebra.LAPACK.syconv!
LinearAlgebra.LAPACK.sysv!
LinearAlgebra.LAPACK.sytrf!
LinearAlgebra.LAPACK.sytri!
LinearAlgebra.LAPACK.sytrs!
LinearAlgebra.LAPACK.hesv!
LinearAlgebra.LAPACK.hetrf!
LinearAlgebra.LAPACK.hetri!
LinearAlgebra.LAPACK.hetrs!
LinearAlgebra.LAPACK.syev!
LinearAlgebra.LAPACK.syevr!
LinearAlgebra.LAPACK.syevd!
LinearAlgebra.LAPACK.sygvd!
LinearAlgebra.LAPACK.bdsqr!
LinearAlgebra.LAPACK.bdsdc!
LinearAlgebra.LAPACK.gecon!
LinearAlgebra.LAPACK.gehrd!
LinearAlgebra.LAPACK.orghr!
LinearAlgebra.LAPACK.gees!
LinearAlgebra.LAPACK.gges!
LinearAlgebra.LAPACK.gges3!
LinearAlgebra.LAPACK.trexc!
LinearAlgebra.LAPACK.trsen!
LinearAlgebra.LAPACK.tgsen!
LinearAlgebra.LAPACK.trsyl!
LinearAlgebra.LAPACK.hseqr!
```

```@meta
DocTestSetup = nothing
```
