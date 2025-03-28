```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/LinearAlgebra/docs/src/index.md"
```

# [Linear Algebra](@id man-linalg)

```@meta
DocTestSetup = :(using LinearAlgebra)
```

Además de (y como parte de) su soporte para arreglos multidimensionales, Julia proporciona implementaciones nativas de muchas operaciones de álgebra lineal comunes y útiles que se pueden cargar con `using LinearAlgebra`. Las operaciones básicas, como [`tr`](@ref), [`det`](@ref) y [`inv`](@ref) son todas compatibles:

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

Así como otras operaciones útiles, como encontrar valores propios o vectores propios:

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

Además, Julia proporciona muchas [factorizations](@ref man-linalg-factorizations) que se pueden utilizar para acelerar problemas como la resolución lineal o la exponenciación de matrices al pre-factorizar una matriz en una forma más adecuada (por razones de rendimiento o memoria) para el problema. Consulte la documentación sobre [`factorize`](@ref) para obtener más información. Como ejemplo:

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

Dado que `A` no es hermítica, simétrica, triangular, tridiagonal o bidiagonal, una factorización LU puede ser lo mejor que podamos hacer. Comparar con:

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

Aquí, Julia pudo detectar que `B` es en realidad simétrico y utilizó una factorización más apropiada. A menudo es posible escribir código más eficiente para una matriz que se sabe que tiene ciertas propiedades, por ejemplo, que es simétrica o tridiagonal. Julia proporciona algunos tipos especiales para que puedas "etiquetar" matrices como que tienen estas propiedades. Por ejemplo:

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

`sB` ha sido etiquetada como una matriz que es (real) simétrica, por lo que para las operaciones posteriores que podríamos realizar en ella, como la eigenfactorización o el cálculo de productos matriz-vector, se pueden encontrar eficiencias al referirse solo a la mitad de ella. Por ejemplo:

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

La operación `\` aquí realiza la solución lineal. El operador de división a la izquierda es bastante poderoso y es fácil escribir código compacto y legible que sea lo suficientemente flexible como para resolver todo tipo de sistemas de ecuaciones lineales.

## Special matrices

[Matrices with special symmetries and structures](https://www2.imm.dtu.dk/pubdb/views/publication_details.php?id=3274) surgen a menudo en álgebra lineal y se asocian frecuentemente con varias factorizaciones de matrices. Julia cuenta con una rica colección de tipos de matrices especiales, que permiten un cálculo rápido con rutinas especializadas que se desarrollan específicamente para tipos de matrices particulares.

Las siguientes tablas resumen los tipos de matrices especiales que se han implementado en Julia, así como si hay ganchos para varios métodos optimizados para ellas en LAPACK.

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

Leyenda:

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

Leyenda:

| Key          | Description                                                                                                                     | Example              |
|:------------ |:------------------------------------------------------------------------------------------------------------------------------- |:-------------------- |
| A (all)      | An optimized method to find all the characteristic values and/or vectors is available                                           | e.g. `eigvals(M)`    |
| R (range)    | An optimized method to find the `il`th through the `ih`th characteristic values are available                                   | `eigvals(M, il, ih)` |
| I (interval) | An optimized method to find the characteristic values in the interval [`vl`, `vh`] is available                                 | `eigvals(M, vl, vh)` |
| V (vectors)  | An optimized method to find the characteristic vectors corresponding to the characteristic values `x=[x1, x2,...]` is available | `eigvecs(M, x)`      |

### The uniform scaling operator

Un operador [`UniformScaling`](@ref) representa un escalar multiplicado por el operador identidad, `λ*I`. El operador identidad `I` se define como una constante y es una instancia de `UniformScaling`. El tamaño de estos operadores es genérico y coincide con la otra matriz en las operaciones binarias [`+`](@ref), [`-`](@ref), [`*`](@ref) y [`\`](@ref). Para `A+I` y `A-I`, esto significa que `A` debe ser cuadrada. La multiplicación con el operador identidad `I` es una operación sin efecto (excepto para verificar que el factor de escalado sea uno) y, por lo tanto, casi sin sobrecarga.

Para ver el operador `UniformScaling` en acción:

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

Si necesitas resolver muchos sistemas de la forma `(A+μI)x = b` para el mismo `A` y diferentes `μ`, podría ser beneficioso calcular primero la factorización de Hessenberg `F` de `A` a través de la función [`hessenberg`](@ref). Dado `F`, Julia emplea un algoritmo eficiente para `(F+μ*I) \ b` (equivalente a `(A+μ*I)x \ b`) y operaciones relacionadas como determinantes.

## [Matrix factorizations](@id man-linalg-factorizations)

[Matrix factorizations (a.k.a. matrix decompositions)](https://en.wikipedia.org/wiki/Matrix_decomposition) calcula la factorización de una matriz en un producto de matrices, y es uno de los conceptos centrales en el álgebra lineal (numérica).

La siguiente tabla resume los tipos de factorizaciones de matrices que se han implementado en Julia. Los detalles de sus métodos asociados se pueden encontrar en la sección [Standard functions](@ref) de la documentación de Álgebra Lineal.

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

Los adjuntos y transpuestos de los objetos [`Factorization`](@ref) se envuelven de manera perezosa en objetos `AdjointFactorization` y `TransposeFactorization`, respectivamente. Genéricamente, el transpuesto de las `Factorization`s reales se envuelven como `AdjointFactorization`.

## [Orthogonal matrices (`AbstractQ`)](@id man-linalg-abstractq)

Algunas factorizaciones de matrices generan factores "matriciales" ortogonales/unitarios. Estas factorizaciones incluyen factorizaciones relacionadas con QR obtenidas de llamadas a [`qr`](@ref), es decir, `QR`, `QRCompactWY` y `QRPivoted`, la factorización de Hessenberg obtenida de llamadas a [`hessenberg`](@ref), y la factorización LQ obtenida de [`lq`](@ref). Si bien estos factores ortogonales/unitarios admiten una representación matricial, su representación interna es, por razones de rendimiento y memoria, diferente. Por lo tanto, deben ser vistos más bien como operadores lineales basados en matrices y basados en funciones. En particular, leer, por ejemplo, una columna de su representación matricial requiere ejecutar código de multiplicación "matriz"-vector, en lugar de simplemente leer datos de la memoria (posiblemente llenando partes del vector con ceros estructurales). Otra clara distinción de otros tipos de matrices no triangulares es que el código de multiplicación subyacente permite la modificación en el lugar durante la multiplicación. Además, los objetos de subtipos específicos de `AbstractQ`, como los creados a través de `4d61726b646f776e2e436f64652822222c202271722229_40726566`, `4d61726b646f776e2e436f64652822222c202268657373656e626572672229_40726566` y `4d61726b646f776e2e436f64652822222c20226c712229_40726566`, pueden comportarse como una matriz cuadrada o rectangular dependiendo del contexto:

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

Debido a esta distinción de matrices densas o estructuradas, el tipo abstracto `AbstractQ` no es un subtipo de `AbstractMatrix`, sino que tiene su propia jerarquía de tipos. Los tipos personalizados que son subtipos de `AbstractQ` pueden confiar en retrocesos genéricos si se satisface la siguiente interfaz. Por ejemplo, para

```julia
struct MyQ{T} <: LinearAlgebra.AbstractQ{T}
    # required fields
end
```

proporcionar sobrecargas para

```julia
Base.size(Q::MyQ) # size of corresponding square matrix representation
Base.convert(::Type{AbstractQ{T}}, Q::MyQ) # eltype promotion [optional]
LinearAlgebra.lmul!(Q::MyQ, x::AbstractVecOrMat) # left-multiplication
LinearAlgebra.rmul!(A::AbstractMatrix, Q::MyQ) # right-multiplication
```

Si la promoción de `eltype` no es de interés, el método `convert` es innecesario, ya que por defecto `convert(::Type{AbstractQ{T}}, Q::AbstractQ{T})` devuelve `Q` mismo. Los adjuntos de objetos de tipo `AbstractQ` se envuelven perezosamente en un tipo de envoltura `AdjointQ`, que requiere sus propios métodos `LinearAlgebra.lmul!` y `LinearAlgebra.rmul!`. Dado este conjunto de métodos, cualquier `Q::MyQ` puede ser utilizado como una matriz, preferiblemente en un contexto multiplicativo: la multiplicación a través de `*` con escalares, vectores y matrices desde la izquierda y la derecha, obtener una representación matricial de `Q` a través de `Matrix(Q)` (o `Q*I`) y la indexación en la representación matricial funcionan. En contraste, la adición y sustracción, así como de manera más general la difusión sobre los elementos en la representación matricial, fallan porque eso sería altamente ineficiente. Para tales casos de uso, considera calcular la representación matricial de antemano y almacenarla en caché para su reutilización futura.

## [Pivoting Strategies](@id man-linalg-pivoting-strategies)

Varios de los [matrix factorizations](@ref man-linalg-factorizations) soportan [pivoting](https://en.wikipedia.org/wiki/Pivot_element), que se puede utilizar para mejorar su estabilidad numérica. De hecho, algunas factorizaciones de matrices, como la factorización LU, pueden fallar sin pivoteo.

In pivoting, first, a [pivot element](https://en.wikipedia.org/wiki/Pivot_element) with good numerical properties is chosen based on a pivoting strategy. Next, the rows and columns of the original matrix are permuted to bring the chosen element in place for subsequent computation. Furthermore, the process is repeated for each stage of the factorization.

En consecuencia, además de los factores de matriz convencionales, las salidas de los esquemas de factorización pivotada también incluyen matrices de permutación.

A continuación, se describen brevemente las estrategias de pivoteo implementadas en Julia. Tenga en cuenta que no todas las factorizaciones de matrices pueden soportarlas. Consulte la documentación de la respectiva [matrix factorization](@ref man-linalg-factorizations) para obtener detalles sobre las estrategias de pivoteo admitidas.

Vea también [`LinearAlgebra.ZeroPivotException`](@ref).

```@docs
LinearAlgebra.NoPivot
LinearAlgebra.RowNonZero
LinearAlgebra.RowMaximum
LinearAlgebra.ColumnNorm
```

## Standard functions

Las funciones de álgebra lineal en Julia se implementan en gran medida llamando a funciones de [LAPACK](https://www.netlib.org/lapack/). Las factorizaciones de matrices dispersas llaman a funciones de [SuiteSparse](http://suitesparse.com). Otros solucionadores dispersos están disponibles como paquetes de Julia.

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

En muchos casos, hay versiones in situ de las operaciones de matrices que te permiten proporcionar un vector o matriz de salida preasignado. Esto es útil al optimizar código crítico para evitar la sobrecarga de asignaciones repetidas. Estas operaciones in situ están sufijadas con `!` a continuación (por ejemplo, `mul!`) de acuerdo con la convención habitual de Julia.

```@docs
LinearAlgebra.mul!
LinearAlgebra.lmul!
LinearAlgebra.rmul!
LinearAlgebra.ldiv!
LinearAlgebra.rdiv!
```

## BLAS functions

En Julia (como en gran parte de la computación científica), las operaciones de álgebra lineal densa se basan en el [LAPACK library](https://www.netlib.org/lapack/), que a su vez se construye sobre bloques de construcción básicos de álgebra lineal conocidos como el [BLAS](https://www.netlib.org/blas/). Hay implementaciones altamente optimizadas de BLAS disponibles para cada arquitectura de computadora, y a veces en rutinas de álgebra lineal de alto rendimiento es útil llamar a las funciones de BLAS directamente.

`LinearAlgebra.BLAS` proporciona envolturas para algunas de las funciones BLAS. Aquellas funciones BLAS que sobrescriben uno de los arreglos de entrada tienen nombres que terminan en `'!'`. Por lo general, una función BLAS tiene cuatro métodos definidos, para [`Float32`](@ref), [`Float64`](@ref), [`ComplexF32`](@ref Complex), y [`ComplexF64`](@ref Complex) arreglos.

### [BLAS character arguments](@id stdlib-blas-chars)

Muchas funciones BLAS aceptan argumentos que determinan si se debe transponer un argumento (`trans`), qué triángulo de una matriz se debe referenciar (`uplo` o `ul`), si se puede asumir que la diagonal de una matriz triangular es toda de unos (`dA`) o en qué lado de una multiplicación de matrices pertenece el argumento de entrada (`side`). Las posibilidades son:

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

Las funciones BLAS se pueden dividir en tres grupos, también llamados tres niveles, dependiendo de cuándo se propusieron por primera vez, el tipo de parámetros de entrada y la complejidad de la operación.

### Level 1 BLAS functions

Las funciones BLAS de nivel 1 fueron propuestas por primera vez en [(Lawson, 1979)][Lawson-1979] y definen operaciones entre escalares y vectores.

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

Las funciones BLAS de nivel 2 se publicaron en [(Dongarra, 1988)][Dongarra-1988] y definen operaciones de matriz-vector.

[Dongarra-1988]: https://dl.acm.org/doi/10.1145/42288.42291

**devolver un vector**

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

**devolver una matriz**

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

Las funciones BLAS de nivel 3 se publicaron en [(Dongarra, 1990)][Dongarra-1990] y definen operaciones de matriz-matriz.

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

`LinearAlgebra.LAPACK` proporciona envolturas para algunas de las funciones de LAPACK para álgebra lineal. Aquellas funciones que sobrescriben uno de los arreglos de entrada tienen nombres que terminan en `'!'`.

Normalmente, una función tiene 4 métodos definidos, uno para cada uno de [`Float64`](@ref), [`Float32`](@ref), arreglos `ComplexF64` y `ComplexF32`.

Tenga en cuenta que la API de LAPACK proporcionada por Julia puede y cambiará en el futuro. Dado que esta API no está orientada al usuario, no hay un compromiso de soportar/depreciar este conjunto específico de funciones en futuras versiones.

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
