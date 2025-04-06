```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/LinearAlgebra/docs/src/index.md"
```

# [Linear Algebra](@id man-linalg)

```@meta
DocTestSetup = :(using LinearAlgebra)
```

Bunun yanı sıra (ve bir parçası olarak) çok boyutlu dizilere desteğinin yanı sıra, Julia, `using LinearAlgebra` ile yüklenebilen birçok yaygın ve kullanışlı lineer cebir işleminin yerel uygulamalarını sağlar. [`tr`](@ref), [`det`](@ref) ve [`inv`](@ref) gibi temel işlemler desteklenmektedir:

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

Eigen değerleri veya öz vektörler bulmak gibi diğer yararlı işlemler de vardır:

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

Ek olarak, Julia birçok [factorizations](@ref man-linalg-factorizations) sağlar; bu, bir matrisin daha uygun bir forma (performans veya bellek nedenleriyle) önceden faktörleştirilmesi yoluyla doğrusal çözüm veya matris üstel hesaplama gibi problemleri hızlandırmak için kullanılabilir. Daha fazla bilgi için [`factorize`](@ref) üzerindeki belgeleri inceleyin. Bir örnek olarak:

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

`A` Hermitian, simetrik, üçgen, üçlü diagonal veya iki diagonal olmadığı için, LU faktörlemesi en iyi yapabileceğimiz şey olabilir. Şunlarla karşılaştırın:

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

Burada, Julia'nın `B` matrisinin aslında simetrik olduğunu tespit edebildiği ve daha uygun bir faktorizasyon kullandığı görülmektedir. Genellikle, belirli özelliklere sahip olduğu bilinen bir matris için daha verimli kod yazmak mümkündür; örneğin, simetrik veya üçgen matris. Julia, bu özelliklere sahip matrisleri "etiketlemek" için bazı özel türler sağlar. Örneğin:

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

`sB` bir (gerçek) simetrik matris olarak etiketlendi, bu nedenle üzerinde daha sonra gerçekleştirebileceğimiz işlemler için, örneğin özdeğer ayrıştırması veya matris-vektör çarpımları gibi, yalnızca yarısını referans alarak verimlilikler elde edilebilir. Örneğin:

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

`\` işlemi burada lineer çözümü gerçekleştirir. Sol bölme operatörü oldukça güçlüdür ve her türlü lineer denklem sistemini çözmek için yeterince esnek, kompakt ve okunabilir kod yazmak kolaydır.

## Special matrices

[Matrices with special symmetries and structures](https://www2.imm.dtu.dk/pubdb/views/publication_details.php?id=3274) lineer cebirde sıkça ortaya çıkar ve çeşitli matris faktorizasyonları ile sıklıkla ilişkilendirilir. Julia, belirli matris türleri için özel olarak geliştirilmiş özel rutinlerle hızlı hesaplama sağlayan zengin bir özel matris türleri koleksiyonu sunar.

Aşağıdaki tablolar, Julia'da uygulanmış özel matris türlerini ve bunlar için LAPACK'te çeşitli optimize edilmiş yöntemlere erişim olup olmadığını özetlemektedir.

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

Efsane:

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

Efsane:

| Key          | Description                                                                                                                     | Example              |
|:------------ |:------------------------------------------------------------------------------------------------------------------------------- |:-------------------- |
| A (all)      | An optimized method to find all the characteristic values and/or vectors is available                                           | e.g. `eigvals(M)`    |
| R (range)    | An optimized method to find the `il`th through the `ih`th characteristic values are available                                   | `eigvals(M, il, ih)` |
| I (interval) | An optimized method to find the characteristic values in the interval [`vl`, `vh`] is available                                 | `eigvals(M, vl, vh)` |
| V (vectors)  | An optimized method to find the characteristic vectors corresponding to the characteristic values `x=[x1, x2,...]` is available | `eigvecs(M, x)`      |

### The uniform scaling operator

Bir [`UniformScaling`](@ref) operatörü, bir skalar ile kimlik operatörünü temsil eder, `λ*I`. Kimlik operatörü `I`, bir sabit olarak tanımlanır ve `UniformScaling`'in bir örneğidir. Bu operatörlerin boyutları genel olup, ikili işlemlerdeki diğer matrislerle eşleşir: [`+`](@ref), [`-`](@ref), [`*`](@ref) ve [`\`](@ref). `A+I` ve `A-I` için bu, `A`'nın kare olması gerektiği anlamına gelir. Kimlik operatörü `I` ile çarpma, bir noop'tur (ölçekleme faktörünün bir olduğunu kontrol etmek dışında) ve bu nedenle neredeyse hiçbir ek yük getirmez.

`UniformScaling` operatörünü eylemde görmek için:

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

If you need to solve many systems of the form `(A+μI)x = b` for the same `A` and different `μ`, it might be beneficial to first compute the Hessenberg factorization `F` of `A` via the [`hessenberg`](@ref) function. Given `F`, Julia employs an efficient algorithm for `(F+μ*I) \ b` (equivalent to `(A+μ*I)x \ b`) and related operations like determinants.

## [Matrix factorizations](@id man-linalg-factorizations)

[Matrix factorizations (a.k.a. matrix decompositions)](https://en.wikipedia.org/wiki/Matrix_decomposition) bir matrisin matrislerin çarpımı olarak faktörizasyonunu hesaplamak ve (sayısal) lineer cebirin merkezi kavramlarından biridir.

Aşağıdaki tablo, Julia'da uygulanmış matris faktorizasyon türlerini özetlemektedir. İlgili yöntemlerin detayları, Lineer Cebir belgelerinin [Standard functions](@ref) bölümünde bulunabilir.

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

[`Factorization`](@ref) nesnelerinin adjoint ve transpoze işlemleri sırasıyla `AdjointFactorization` ve `TransposeFactorization` nesneleri içinde tembel bir şekilde sarılır. Genel olarak, gerçek `Factorization`ların transpoze işlemleri `AdjointFactorization` olarak sarılır.

## [Orthogonal matrices (`AbstractQ`)](@id man-linalg-abstractq)

Bazı matris faktorizasyonları ortogonal/üniter "matris" faktörleri üretir. Bu faktorizasyonlar, [`qr`](@ref) çağrılarından elde edilen QR ile ilgili faktorizasyonları, yani `QR`, `QRCompactWY` ve `QRPivoted`, [`hessenberg`](@ref) çağrılarından elde edilen Hessenberg faktorizasyonu ve [`lq`](@ref) ile elde edilen LQ faktorizasyonunu içerir. Bu ortogonal/üniter faktörler bir matris temsilini kabul etse de, içsel temsilleri performans ve bellek nedenleriyle farklıdır. Bu nedenle, daha çok matris destekli, fonksiyon tabanlı lineer operatörler olarak görülmelidirler. Özellikle, örneğin, matris temsilinin bir sütununu okumak, verileri bellekten basitçe okumak (muhtemelen vektörün bazı kısımlarını yapısal sıfırlarla doldurarak) yerine "matris"-vektör çarpma kodunu çalıştırmayı gerektirir. Diğer, üçgen olmayan matris türlerinden bir diğer belirgin ayrım, temel çarpma kodunun çarpma sırasında yerinde değişiklik yapmaya izin vermesidir. Ayrıca, `4d61726b646f776e2e436f64652822222c202271722229_40726566`, `4d61726b646f776e2e436f64652822222c202268657373656e626572672229_40726566` ve `4d61726b646f776e2e436f64652822222c20226c712229_40726566` aracılığıyla oluşturulan belirli `AbstractQ` alt türlerinin bağlama bağlı olarak kare veya dikdörtgen bir matris gibi davranabileceği de belirtilmelidir:

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

Bu yoğun veya yapılandırılmış matrislerden bu ayrım nedeniyle, soyut `AbstractQ` türü `AbstractMatrix` alt türü değildir, bunun yerine kendi tür hiyerarşisine sahiptir. `AbstractQ` alt türü olan özel türler, aşağıdaki arayüz karşılandığında genel geri dönüşlere güvenebilir. Örneğin, için

```julia
struct MyQ{T} <: LinearAlgebra.AbstractQ{T}
    # required fields
end
```

aşırı yüklemeleri sağlayın

```julia
Base.size(Q::MyQ) # size of corresponding square matrix representation
Base.convert(::Type{AbstractQ{T}}, Q::MyQ) # eltype promotion [optional]
LinearAlgebra.lmul!(Q::MyQ, x::AbstractVecOrMat) # left-multiplication
LinearAlgebra.rmul!(A::AbstractMatrix, Q::MyQ) # right-multiplication
```

Eğer `eltype` yükseltmesi ilginizi çekmiyorsa, `convert` yöntemi gereksizdir, çünkü varsayılan olarak `convert(::Type{AbstractQ{T}}, Q::AbstractQ{T})` `Q`'yu kendisi olarak döndürür. `AbstractQ` türündeki nesnelerin adjoint'leri, kendi `LinearAlgebra.lmul!` ve `LinearAlgebra.rmul!` yöntemlerini gerektiren bir `AdjointQ` sarmalayıcı türünde tembel bir şekilde sarılır. Bu yöntemler seti ile, herhangi bir `Q::MyQ` bir matris gibi kullanılabilir, tercihen çarpan bir bağlamda: skalarlar, vektörler ve matrislerle soldan ve sağdan `*` ile çarpma, `Matrix(Q)` (veya `Q*I`) ile `Q`'nun matris temsilini elde etme ve matris temsiline indeksleme gibi işlemler çalışır. Buna karşılık, toplama ve çıkarma ile daha genel olarak matris temsilindeki elemanlar üzerinde yayılma işlemleri başarısız olur çünkü bu son derece verimsiz olur. Bu tür kullanım durumları için, matris temsilini önceden hesaplamayı ve gelecekteki yeniden kullanım için önbelleğe almayı düşünün.

## [Pivoting Strategies](@id man-linalg-pivoting-strategies)

Julia'nın [matrix factorizations](@ref man-linalg-factorizations) birkaç [pivoting](https://en.wikipedia.org/wiki/Pivot_element) desteği vardır; bu, sayısal kararlılıklarını artırmak için kullanılabilir. Aslında, LU faktorizasyonu gibi bazı matris faktorizasyonları, pivotlama olmadan başarısız olabilir.

In pivoting, first, a [pivot element](https://en.wikipedia.org/wiki/Pivot_element) with good numerical properties is chosen based on a pivoting strategy. Next, the rows and columns of the original matrix are permuted to bring the chosen element in place for subsequent computation. Furthermore, the process is repeated for each stage of the factorization.

Sonuç olarak, geleneksel matris faktörlerinin yanı sıra, pivotlu faktorizasyon şemalarının çıktıları da permütasyon matrislerini içerir.

Aşağıda, Julia'da uygulanan pivotlama stratejileri kısaca açıklanmaktadır. Tüm matris faktörizasyonlarının bunları desteklemeyebileceğini unutmayın. Desteklenen pivotlama stratejileri hakkında ayrıntılar için ilgili [matrix factorization](@ref man-linalg-factorizations) belgesine başvurun.

Ayrıca bkz. [`LinearAlgebra.ZeroPivotException`](@ref).

```@docs
LinearAlgebra.NoPivot
LinearAlgebra.RowNonZero
LinearAlgebra.RowMaximum
LinearAlgebra.ColumnNorm
```

## Standard functions

Lineer cebir fonksiyonları Julia'da büyük ölçüde [LAPACK](https://www.netlib.org/lapack/) fonksiyonlarını çağırarak uygulanmaktadır. Seyrek matris faktorizasyonları [SuiteSparse](http://suitesparse.com) fonksiyonlarını çağırmaktadır. Diğer seyrek çözücüler Julia paketleri olarak mevcuttur.

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

Birçok durumda, önceden tahsis edilmiş bir çıktı vektörü veya matris sağlayarak yerinde matris işlemleri yapmanıza olanak tanıyan yerinde sürümleri vardır. Bu, tekrar eden tahsislerin aşamasını önlemek için kritik kodu optimize ederken faydalıdır. Bu yerinde işlemler, aşağıda `!` ile sonlandırılmıştır (örneğin, `mul!`), bu da alışılmış Julia geleneğine göre yapılmıştır.

```@docs
LinearAlgebra.mul!
LinearAlgebra.lmul!
LinearAlgebra.rmul!
LinearAlgebra.ldiv!
LinearAlgebra.rdiv!
```

## BLAS functions

Julia (bilimsel hesaplamanın çoğunda olduğu gibi), yoğun lineer cebir işlemleri [LAPACK library](https://www.netlib.org/lapack/) üzerine kuruludur; bu da temel lineer cebir yapı taşları olarak bilinen [BLAS](https://www.netlib.org/blas/) üzerine inşa edilmiştir. Her bilgisayar mimarisi için mevcut olan yüksek optimize edilmiş BLAS uygulamaları vardır ve bazen yüksek performanslı lineer cebir rutinlerinde BLAS fonksiyonlarını doğrudan çağırmak faydalı olabilir.

`LinearAlgebra.BLAS`, bazı BLAS fonksiyonları için sarmalayıcılar sağlar. Girdi dizilerinden birini değiştiren BLAS fonksiyonlarının isimleri `'!'` ile biter. Genellikle, bir BLAS fonksiyonunun [`Float32`](@ref), [`Float64`](@ref), [`ComplexF32`](@ref Complex) ve [`ComplexF64`](@ref Complex) dizileri için dört yöntemi tanımlanmıştır.

### [BLAS character arguments](@id stdlib-blas-chars)

Birçok BLAS fonksiyonu, bir argümanın transpoze edilip edilmeyeceğini belirleyen (`trans`), bir matrisin hangi üçgeninin referans alınacağını (`uplo` veya `ul`), bir üçgen matrisin köşegeninin hepsinin bir olduğu varsayımının yapılıp yapılamayacağını (`dA`) veya bir matris çarpımında girdi argümanının hangi tarafta yer aldığını (`side`) belirleyen argümanlar kabul eder. Olasılıklar şunlardır:

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

BLAS fonksiyonları, ilk olarak önerildikleri zamana, girdi parametrelerinin türüne ve işlemin karmaşıklığına bağlı olarak üç gruba, yani üç seviyeye ayrılabilir.

### Level 1 BLAS functions

Seviye 1 BLAS fonksiyonları ilk olarak [(Lawson, 1979)][Lawson-1979] yılında önerilmiştir ve skalarlar ile vektörler arasındaki işlemleri tanımlar.

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

Seviye 2 BLAS fonksiyonları [(Dongarra, 1988)][Dongarra-1988] tarihinde yayımlandı ve matris-vektör işlemlerini tanımlar.

[Dongarra-1988]: https://dl.acm.org/doi/10.1145/42288.42291

**bir vektör döndür**

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

**bir matris döndür**

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

Seviye 3 BLAS fonksiyonları [(Dongarra, 1990)][Dongarra-1990] tarihinde yayımlandı ve matris-matris işlemlerini tanımlar.

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

`LinearAlgebra.LAPACK`, lineer cebir için bazı LAPACK fonksiyonları için sarmalayıcılar sağlar. Girdi dizilerinden birini değiştiren o fonksiyonların isimleri `'!'` ile biter.

Genellikle bir fonksiyonun tanımlı 4 yöntemi vardır, her biri için [`Float64`](@ref), [`Float32`](@ref), `ComplexF64` ve `ComplexF32` dizileri.

LAPACK API'sinin Julia tarafından sağlandığını ve gelecekte değişebileceğini unutmayın. Bu API kullanıcıya açık olmadığından, gelecekteki sürümlerde bu belirli işlev setini destekleme/iptal etme taahhüdü yoktur.

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
