```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/LinearAlgebra/docs/src/index.md"
```

# [Linear Algebra](@id man-linalg)

```@meta
DocTestSetup = :(using LinearAlgebra)
```

다차원 배열에 대한 지원의 일환으로, Julia는 `using LinearAlgebra`를 통해 로드할 수 있는 많은 일반적이고 유용한 선형 대수 연산의 네이티브 구현을 제공합니다. [`tr`](@ref), [`det`](@ref), 및 [`inv`](@ref)와 같은 기본 연산이 모두 지원됩니다:

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

고유값이나 고유벡터를 찾는 것과 같은 다른 유용한 작업들:

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

또한, Julia는 선형 해결 또는 행렬 지수화와 같은 문제를 가속화하는 데 사용할 수 있는 많은 [factorizations](@ref man-linalg-factorizations)를 제공합니다. 이는 문제에 더 적합한 형태로 행렬을 사전 인수 분해하여 성능이나 메모리 측면에서 유리하게 만들 수 있습니다. 자세한 내용은 [`factorize`](@ref)에 대한 문서를 참조하십시오. 예를 들어:

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

`A`가 에르미트가 아니고, 대칭도 아니며, 삼각형, 삼중 대각선 또는 이중 대각선도 아니기 때문에 LU 분해가 우리가 할 수 있는 최선일 수 있습니다. 다음과 비교하십시오:

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

여기서 줄리아는 `B`가 실제로 대칭임을 감지하고 더 적절한 인수분해를 사용했습니다. 종종 특정 속성을 가진 행렬에 대해 더 효율적인 코드를 작성하는 것이 가능합니다. 예를 들어, 대칭이거나 삼중 대각선인 경우입니다. 줄리아는 이러한 속성을 가진 행렬을 "태그"할 수 있도록 몇 가지 특수 유형을 제공합니다. 예를 들어:

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

`sB`는 (실수) 대칭 행렬로 태그가 지정되었으므로, 고유 분해나 행렬-벡터 곱과 같은 이후의 작업을 수행할 때, 그 절반만 참조함으로써 효율성을 찾을 수 있습니다. 예를 들어:

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

`\` 연산자는 여기서 선형 솔루션을 수행합니다. 왼쪽 나눗셈 연산자는 매우 강력하며, 모든 종류의 선형 방정식 시스템을 해결할 수 있을 만큼 유연한 간결하고 읽기 쉬운 코드를 작성하기가 쉽습니다.

## Special matrices

[Matrices with special symmetries and structures](https://www2.imm.dtu.dk/pubdb/views/publication_details.php?id=3274)는 선형 대수에서 자주 발생하며 다양한 행렬 분해와 자주 연관됩니다. Julia는 특정 행렬 유형을 위해 특별히 개발된 전문 루틴을 사용하여 빠른 계산을 가능하게 하는 다양한 특수 행렬 유형의 풍부한 컬렉션을 제공합니다.

다음 표는 Julia에서 구현된 특수 행렬의 유형과 LAPACK에서 이를 위한 다양한 최적화된 방법에 대한 후크가 사용 가능한지 여부를 요약합니다.

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

전설:

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

전설:

| Key          | Description                                                                                                                     | Example              |
|:------------ |:------------------------------------------------------------------------------------------------------------------------------- |:-------------------- |
| A (all)      | An optimized method to find all the characteristic values and/or vectors is available                                           | e.g. `eigvals(M)`    |
| R (range)    | An optimized method to find the `il`th through the `ih`th characteristic values are available                                   | `eigvals(M, il, ih)` |
| I (interval) | An optimized method to find the characteristic values in the interval [`vl`, `vh`] is available                                 | `eigvals(M, vl, vh)` |
| V (vectors)  | An optimized method to find the characteristic vectors corresponding to the characteristic values `x=[x1, x2,...]` is available | `eigvecs(M, x)`      |

### The uniform scaling operator

A [`UniformScaling`](@ref) 연산자는 스칼라와 항등 연산자 `λ*I`를 나타냅니다. 항등 연산자 `I`는 상수로 정의되며 `UniformScaling`의 인스턴스입니다. 이러한 연산자의 크기는 일반적이며 이진 연산 [`+`](@ref), [`-`](@ref), [`*`](@ref) 및 [`\`](@ref)의 다른 행렬과 일치합니다. `A+I` 및 `A-I`의 경우, `A`는 정방행렬이어야 합니다. 항등 연산자 `I`와의 곱셈은 noop이며 (스케일링 인자가 1인지 확인하는 것을 제외하고) 따라서 거의 오버헤드가 없습니다.

`UniformScaling` 연산자를 사용하는 방법:

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

같은 `A`에 대해 다른 `μ`에 대한 `(A+μI)x = b` 형태의 많은 시스템을 해결해야 하는 경우, 먼저 [`hessenberg`](@ref) 함수를 통해 `A`의 헤센베르크 분해 `F`를 계산하는 것이 유리할 수 있습니다. `F`가 주어지면, Julia는 `(F+μ*I) \ b` (이는 `(A+μ*I)x \ b`와 동등함)에 대한 효율적인 알고리즘과 행렬식과 같은 관련 연산을 사용합니다.

## [Matrix factorizations](@id man-linalg-factorizations)

[Matrix factorizations (a.k.a. matrix decompositions)](https://en.wikipedia.org/wiki/Matrix_decomposition) 행렬을 행렬의 곱으로 분해하는 것을 계산하며, 이는 (수치) 선형 대수의 중심 개념 중 하나입니다.

다음 표는 Julia에서 구현된 행렬 분해의 유형을 요약한 것입니다. 관련된 방법에 대한 세부정보는 선형 대수 문서의 [Standard functions](@ref) 섹션에서 확인할 수 있습니다.

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

[`Factorization`](@ref) 객체의 어드전트와 전치는 각각 `AdjointFactorization` 및 `TransposeFactorization` 객체로 지연 래핑됩니다. 일반적으로, 실수 `Factorization`의 전치는 `AdjointFactorization`으로 래핑됩니다.

## [Orthogonal matrices (`AbstractQ`)](@id man-linalg-abstractq)

일부 행렬 분해는 직교/유니타리 "행렬" 요소를 생성합니다. 이러한 분해에는 [`qr`](@ref) 호출에서 얻은 QR 관련 분해, 즉 `QR`, `QRCompactWY` 및 `QRPivoted`, [`hessenberg`](@ref) 호출에서 얻은 헤센베르크 분해, 그리고 [`lq`](@ref)에서 얻은 LQ 분해가 포함됩니다. 이러한 직교/유니타리 요소는 행렬 표현을 허용하지만, 성능 및 메모리 이유로 내부 표현은 다릅니다. 따라서 이들은 행렬 기반의 함수 기반 선형 연산자로 보는 것이 더 적절합니다. 특히, 예를 들어 행렬 표현의 열을 읽는 것은 메모리에서 데이터를 단순히 읽어오는 것이 아니라 "행렬"-벡터 곱셈 코드를 실행해야 합니다(가능한 경우 벡터의 일부를 구조적 제로로 채우는 것). 다른 비삼각형 행렬 유형과의 또 다른 명확한 구별은 기본 곱셈 코드가 곱셈 중에 제자리 수정을 허용한다는 점입니다. 또한 `4d61726b646f776e2e436f64652822222c202271722229_40726566`, `4d61726b646f776e2e436f64652822222c202268657373656e626572672229_40726566` 및 `4d61726b646f776e2e436f64652822222c20226c712229_40726566`를 통해 생성된 특정 `AbstractQ` 하위 유형의 객체는 상황에 따라 정사각형 또는 직사각형 행렬처럼 동작할 수 있습니다:

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

이 밀집 또는 구조화된 행렬과의 구별로 인해, 추상 `AbstractQ` 타입은 `AbstractMatrix`의 하위 타입이 아니며, 대신 자체 타입 계층을 가지고 있습니다. `AbstractQ`를 하위 타입으로 하는 사용자 정의 타입은 다음 인터페이스가 충족되면 일반적인 대체 기능에 의존할 수 있습니다. 예를 들어,

```julia
struct MyQ{T} <: LinearAlgebra.AbstractQ{T}
    # required fields
end
```

오버로드 제공하기

```julia
Base.size(Q::MyQ) # size of corresponding square matrix representation
Base.convert(::Type{AbstractQ{T}}, Q::MyQ) # eltype promotion [optional]
LinearAlgebra.lmul!(Q::MyQ, x::AbstractVecOrMat) # left-multiplication
LinearAlgebra.rmul!(A::AbstractMatrix, Q::MyQ) # right-multiplication
```

`eltype` 승격이 관심이 없다면, `convert` 메소드는 필요하지 않습니다. 기본적으로 `convert(::Type{AbstractQ{T}}, Q::AbstractQ{T})`는 `Q` 자체를 반환합니다. `AbstractQ` 타입 객체의 어드전트는 `AdjointQ` 래퍼 타입으로 지연 래핑되며, 이는 자체 `LinearAlgebra.lmul!` 및 `LinearAlgebra.rmul!` 메소드를 필요로 합니다. 이러한 메소드 집합을 고려할 때, 어떤 `Q::MyQ`도 행렬처럼 사용할 수 있으며, 특히 곱셈 맥락에서 사용되는 것이 바람직합니다: 스칼라, 벡터 및 행렬과의 왼쪽 및 오른쪽 곱셈을 위한 `*`를 통한 곱셈, `Matrix(Q)` (또는 `Q*I`)를 통해 `Q`의 행렬 표현을 얻고, 행렬 표현에 인덱싱하는 모든 작업이 가능합니다. 반면, 덧셈 및 뺄셈, 그리고 행렬 표현의 요소에 대한 브로드캐스팅은 비효율적이기 때문에 실패합니다. 이러한 사용 사례에 대해서는 행렬 표현을 미리 계산하고 향후 재사용을 위해 캐시하는 것을 고려하십시오.

## [Pivoting Strategies](@id man-linalg-pivoting-strategies)

줄리아의 [matrix factorizations](@ref man-linalg-factorizations) 여러 개는 [pivoting](https://en.wikipedia.org/wiki/Pivot_element)를 지원하며, 이는 수치적 안정성을 개선하는 데 사용할 수 있습니다. 사실, LU 분해와 같은 일부 행렬 분해는 피벗팅 없이 실패할 수 있습니다.

피벗팅에서 먼저, 피벗팅 전략에 따라 좋은 수치적 특성을 가진 [pivot element](https://en.wikipedia.org/wiki/Pivot_element)가 선택됩니다. 다음으로, 원래 행렬의 행과 열이 재배열되어 선택된 요소가 후속 계산을 위해 제자리에 오도록 합니다. 또한, 이 과정은 인수 분해의 각 단계에 대해 반복됩니다.

결과적으로, 기존의 행렬 인수 외에도 피벗 인수 분해 방식의 출력에는 순열 행렬도 포함됩니다.

다음은 Julia에서 구현된 피벗 전략에 대한 간략한 설명입니다. 모든 행렬 분해가 이를 지원하는 것은 아닙니다. 지원되는 피벗 전략에 대한 자세한 내용은 해당 [matrix factorization](@ref man-linalg-factorizations)의 문서를 참조하십시오.

또한 [`LinearAlgebra.ZeroPivotException`](@ref)를 참조하세요.

```@docs
LinearAlgebra.NoPivot
LinearAlgebra.RowNonZero
LinearAlgebra.RowMaximum
LinearAlgebra.ColumnNorm
```

## Standard functions

줄리아의 선형 대수 함수는 주로 [LAPACK](https://www.netlib.org/lapack/)의 함수를 호출하여 구현됩니다. 희소 행렬 분해는 [SuiteSparse](http://suitesparse.com)의 함수를 호출합니다. 다른 희소 솔버는 줄리아 패키지로 제공됩니다.

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

많은 경우, 미리 할당된 출력 벡터나 행렬을 제공할 수 있는 제자리 버전의 행렬 연산이 있습니다. 이는 반복적인 할당의 오버헤드를 피하기 위해 중요한 코드를 최적화할 때 유용합니다. 이러한 제자리 연산은 일반적인 Julia 관례에 따라 아래에 `!`로 접미사가 붙습니다 (예: `mul!`).

```@docs
LinearAlgebra.mul!
LinearAlgebra.lmul!
LinearAlgebra.rmul!
LinearAlgebra.ldiv!
LinearAlgebra.rdiv!
```

## BLAS functions

줄리아(Julia)에서는(과학 계산의 많은 부분에서) 밀집 선형 대수 연산이 [LAPACK library](https://www.netlib.org/lapack/)를 기반으로 하며, 이는 기본 선형 대수 빌딩 블록으로 알려진 [BLAS](https://www.netlib.org/blas/) 위에 구축됩니다. 모든 컴퓨터 아키텍처에 대해 사용할 수 있는 고도로 최적화된 BLAS 구현이 있으며, 때때로 고성능 선형 대수 루틴에서는 BLAS 함수를 직접 호출하는 것이 유용합니다.

`LinearAlgebra.BLAS`는 일부 BLAS 함수에 대한 래퍼를 제공합니다. 입력 배열 중 하나를 덮어쓰는 BLAS 함수는 이름이 `'!'`로 끝납니다. 일반적으로 BLAS 함수는 [`Float32`](@ref), [`Float64`](@ref), [`ComplexF32`](@ref Complex), 및 [`ComplexF64`](@ref Complex) 배열에 대해 네 가지 메서드가 정의되어 있습니다.

### [BLAS character arguments](@id stdlib-blas-chars)

많은 BLAS 함수는 인수로 전치 여부를 결정하는 인수(`trans`), 참조할 행렬의 삼각형(`uplo` 또는 `ul`), 삼각 행렬의 대각선이 모두 1로 가정될 수 있는지 여부(`dA`), 또는 행렬 곱셈에서 입력 인수가 속하는 쪽(`side`)을 허용합니다. 가능한 옵션은 다음과 같습니다:

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

BLAS 함수는 처음 제안된 시기, 입력 매개변수의 유형 및 연산의 복잡성에 따라 세 그룹, 즉 세 가지 수준으로 나눌 수 있습니다.

### Level 1 BLAS functions

레벨 1 BLAS 함수는 [(Lawson, 1979)][Lawson-1979]에서 처음 제안되었으며, 스칼라와 벡터 간의 연산을 정의합니다.

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

레벨 2 BLAS 함수는 [(Dongarra, 1988)][Dongarra-1988]에 발표되었으며, 행렬-벡터 연산을 정의합니다.

[동가라-1988]: https://dl.acm.org/doi/10.1145/42288.42291

**벡터 반환**

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

**행렬 반환**

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

레벨 3 BLAS 함수는 [(Dongarra, 1990)][Dongarra-1990]에 발표되었으며, 행렬-행렬 연산을 정의합니다.

[동가라-1990]: https://dl.acm.org/doi/10.1145/77626.79170

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

`LinearAlgebra.LAPACK`는 선형 대수를 위한 일부 LAPACK 함수에 대한 래퍼를 제공합니다. 입력 배열 중 하나를 덮어쓰는 함수는 이름이 `'!'`로 끝납니다.

보통 함수는 [`Float64`](@ref), [`Float32`](@ref), `ComplexF64` 및 `ComplexF32` 배열 각각에 대해 정의된 4개의 메서드를 가지고 있습니다.

LAPACK API는 Julia에서 제공되며, 향후 변경될 수 있습니다. 이 API는 사용자에게 노출되지 않기 때문에, 향후 릴리스에서 이 특정 함수 집합을 지원하거나 사용 중단할 것이라는 약속이 없습니다.

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
