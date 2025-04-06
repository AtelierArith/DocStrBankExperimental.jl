```@meta
EditURL = "https://github.com/JuliaSparse/SparseArrays.jl/blob/master/docs/src/index.md"
```

# Sparse Arrays

```@meta
DocTestSetup = :(using SparseArrays, LinearAlgebra)
```

줄리아는 희소 벡터와 [sparse matrices](https://en.wikipedia.org/wiki/Sparse_matrix)를 `SparseArrays` 표준 라이브러리 모듈에서 지원합니다. 희소 배열은 충분한 수의 0을 포함하고 있어, 이를 특별한 데이터 구조에 저장하면 밀집 배열에 비해 공간과 실행 시간에서 절약을 할 수 있습니다.

다양한 희소 저장 유형, 다차원 희소 배열 등을 구현하는 외부 패키지는 [Noteworthy External Sparse Packages](@ref)에서 찾을 수 있습니다.

## [Compressed Sparse Column (CSC) Sparse Matrix Storage](@id man-csc)

줄리아에서 희소 행렬은 [Compressed Sparse Column (CSC) format](https://en.wikipedia.org/wiki/Sparse_matrix#Compressed_sparse_column_.28CSC_or_CCS.29)에 저장됩니다. 줄리아 희소 행렬의 타입은 [`SparseMatrixCSC{Tv,Ti}`](@ref)이며, 여기서 `Tv`는 저장된 값의 타입이고, `Ti`는 열 포인터와 행 인덱스를 저장하기 위한 정수 타입입니다. `SparseMatrixCSC`의 내부 표현은 다음과 같습니다:

```julia
struct SparseMatrixCSC{Tv,Ti<:Integer} <: AbstractSparseMatrixCSC{Tv,Ti}
    m::Int                  # Number of rows
    n::Int                  # Number of columns
    colptr::Vector{Ti}      # Column j is in colptr[j]:(colptr[j+1]-1)
    rowval::Vector{Ti}      # Row indices of stored values
    nzval::Vector{Tv}       # Stored values, typically nonzeros
end
```

압축 희소 열 저장 방식은 희소 행렬의 열에 있는 요소에 쉽게 빠르게 접근할 수 있게 해주지만, 행으로 희소 행렬에 접근하는 것은 상당히 느립니다. CSC 구조에서 이전에 저장되지 않은 항목을 한 번에 하나씩 삽입하는 작업은 느린 경향이 있습니다. 이는 삽입 지점 이후의 희소 행렬의 모든 요소를 한 칸씩 이동해야 하기 때문입니다.

모든 희소 행렬에 대한 연산은 성능을 위해 CSC 데이터 구조를 활용하고 비싼 연산을 피하도록 신중하게 구현됩니다.

CSC 형식의 데이터가 다른 애플리케이션이나 라이브러리에서 온 경우, 이를 줄리아에 가져오려면 1 기반 인덱싱을 사용해야 합니다. 모든 열의 행 인덱스는 정렬되어 있어야 하며, 그렇지 않으면 행렬이 잘못 표시됩니다. `SparseMatrixCSC` 객체에 정렬되지 않은 행 인덱스가 포함되어 있는 경우, 이를 정렬하는 빠른 방법 중 하나는 이중 전치(transpose)를 수행하는 것입니다. 전치 연산은 지연(lazy) 방식으로 수행되므로, 각 전치를 구체화하기 위해 복사본을 만들어야 합니다.

일부 응용 프로그램에서는 `SparseMatrixCSC`에 명시적인 제로 값을 저장하는 것이 편리합니다. 이러한 값은 `Base`의 함수에서 허용되지만, 변형 작업에서 보존된다는 보장은 없습니다. 명시적으로 저장된 제로는 많은 루틴에서 구조적 비제로로 처리됩니다. [`nnz`](@ref) 함수는 비구조적 제로를 포함하여 희소 데이터 구조에 명시적으로 저장된 요소의 수를 반환합니다. 정확한 수치 비제로의 수를 세려면 [`count(!iszero, x)`](@ref)를 사용하여 희소 행렬의 모든 저장된 요소를 검사하십시오. [`dropzeros`](@ref) 및 제자리에서 사용하는 [`dropzeros!`](@ref)는 희소 행렬에서 저장된 제로를 제거하는 데 사용할 수 있습니다.

```jldoctest
julia> A = sparse([1, 1, 2, 3], [1, 3, 2, 3], [0, 1, 2, 0])
3×3 SparseMatrixCSC{Int64, Int64} with 4 stored entries:
 0  ⋅  1
 ⋅  2  ⋅
 ⋅  ⋅  0

julia> dropzeros(A)
3×3 SparseMatrixCSC{Int64, Int64} with 2 stored entries:
 ⋅  ⋅  1
 ⋅  2  ⋅
 ⋅  ⋅  ⋅
```

## Sparse Vector Storage

희소 벡터는 희소 행렬의 압축 희소 열 형식과 유사한 방식으로 저장됩니다. Julia에서 희소 벡터는 [`SparseVector{Tv,Ti}`](@ref) 유형을 가지며, 여기서 `Tv`는 저장된 값의 유형이고 `Ti`는 인덱스의 정수 유형입니다. 내부 표현은 다음과 같습니다:

```julia
struct SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
    n::Int              # Length of the sparse vector
    nzind::Vector{Ti}   # Indices of stored values
    nzval::Vector{Tv}   # Stored values, typically nonzeros
end
```

[`SparseMatrixCSC`](@ref)에 관해서는 `SparseVector` 유형이 명시적으로 저장된 0을 포함할 수 있습니다. (참조: [Sparse Matrix Storage](@ref man-csc).)

## Sparse Vector and Matrix Constructors

희소 배열을 만드는 가장 간단한 방법은 Julia가 밀집 배열을 다루기 위해 제공하는 [`zeros`](@ref) 함수와 동등한 함수를 사용하는 것입니다. 대신 희소 배열을 생성하려면 `sp` 접두사를 붙여 같은 이름을 사용할 수 있습니다:

```jldoctest
julia> spzeros(3)
3-element SparseVector{Float64, Int64} with 0 stored entries
```

[`sparse`](@ref) 함수는 종종 희소 배열을 구성하는 유용한 방법입니다. 예를 들어, 희소 행렬을 구성하기 위해 행 인덱스의 벡터 `I`, 열 인덱스의 벡터 `J`, 저장된 값의 벡터 `V`를 입력할 수 있습니다(이는 [COO (coordinate) format](https://en.wikipedia.org/wiki/Sparse_matrix#Coordinate_list_.28COO.29)로도 알려져 있습니다). 그런 다음 `sparse(I,J,V)`는 `S[I[k], J[k]] = V[k]`가 되도록 희소 행렬을 구성합니다. 동등한 희소 벡터 생성자는 [`sparsevec`](@ref)로, (행) 인덱스 벡터 `I`와 저장된 값이 있는 벡터 `V`를 사용하여 희소 벡터 `R`을 구성하며, `R[I[k]] = V[k]`가 됩니다.

```jldoctest sparse_function
julia> I = [1, 4, 3, 5]; J = [4, 7, 18, 9]; V = [1, 2, -5, 3];

julia> S = sparse(I,J,V)
5×18 SparseMatrixCSC{Int64, Int64} with 4 stored entries:
⎡⠀⠈⠀⠀⠀⠀⠀⠀⢀⎤
⎣⠀⠀⠀⠂⡀⠀⠀⠀⠀⎦

julia> R = sparsevec(I,V)
5-element SparseVector{Int64, Int64} with 4 stored entries:
  [1]  =  1
  [3]  =  -5
  [4]  =  2
  [5]  =  3
```

[`sparse`](@ref) 및 [`sparsevec`](@ref) 함수의 역은 [`findnz`](@ref)로, 이는 희소 배열을 생성하는 데 사용된 입력값(영으로 저장된 항목 포함)을 검색합니다. [`findall(!iszero, x)`](@ref)는 `x`의 비영 항목의 카르테시안 인덱스를 반환합니다(영으로 저장된 항목은 포함하지 않음).

```jldoctest sparse_function
julia> findnz(S)
([1, 4, 5, 3], [4, 7, 9, 18], [1, 2, 3, -5])

julia> findall(!iszero, S)
4-element Vector{CartesianIndex{2}}:
 CartesianIndex(1, 4)
 CartesianIndex(4, 7)
 CartesianIndex(5, 9)
 CartesianIndex(3, 18)

julia> findnz(R)
([1, 3, 4, 5], [1, -5, 2, 3])

julia> findall(!iszero, R)
4-element Vector{Int64}:
 1
 3
 4
 5
```

희소 배열을 생성하는 또 다른 방법은 [`sparse`](@ref) 함수를 사용하여 밀집 배열을 희소 배열로 변환하는 것입니다:

```jldoctest
julia> sparse(Matrix(1.0I, 5, 5))
5×5 SparseMatrixCSC{Float64, Int64} with 5 stored entries:
 1.0   ⋅    ⋅    ⋅    ⋅
  ⋅   1.0   ⋅    ⋅    ⋅
  ⋅    ⋅   1.0   ⋅    ⋅
  ⋅    ⋅    ⋅   1.0   ⋅
  ⋅    ⋅    ⋅    ⋅   1.0

julia> sparse([1.0, 0.0, 1.0])
3-element SparseVector{Float64, Int64} with 2 stored entries:
  [1]  =  1.0
  [3]  =  1.0
```

다른 방향으로 가려면 [`Array`](@ref) 생성자를 사용할 수 있습니다. [`issparse`](@ref) 함수는 행렬이 희소한지 쿼리하는 데 사용할 수 있습니다.

```jldoctest
julia> issparse(spzeros(5))
true
```

## Sparse matrix operations

희소 행렬에 대한 산술 연산은 밀집 행렬에서와 동일하게 작동합니다. 희소 행렬의 인덱싱, 할당 및 연결은 밀집 행렬과 동일한 방식으로 작동합니다. 인덱싱 작업, 특히 할당은 한 번에 하나의 요소를 처리할 때 비용이 많이 듭니다. 많은 경우 희소 행렬을 [`findnz`](@ref) 형식의 `(I,J,V)`로 변환하고, 밀집 벡터 `(I,J,V)`에서 값이나 구조를 조작한 다음, 희소 행렬을 재구성하는 것이 더 나을 수 있습니다.

## Correspondence of dense and sparse methods

다음 표는 희소 행렬의 내장 메서드와 밀집 행렬 유형의 해당 메서드 간의 대응 관계를 제공합니다. 일반적으로 희소 행렬을 생성하는 메서드는 결과 행렬이 주어진 희소 행렬 `S`와 동일한 희소성 패턴을 따르거나, 결과 희소 행렬이 밀도 `d`를 가지며, 즉 각 행렬 요소가 0이 아닐 확률이 `d`인 점에서 밀집 행렬의 대응 메서드와 다릅니다.

자세한 내용은 표준 라이브러리 참조의 [Sparse Vectors and Matrices](@ref stdlib-sparse-arrays) 섹션에서 확인할 수 있습니다.

| Sparse                       | Dense                    | Description                                                                                                                                          |
|:---------------------------- |:------------------------ |:---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`spzeros(m,n)`](@ref)       | [`zeros(m,n)`](@ref)     | Creates a *m*-by-*n* matrix of zeros. ([`spzeros(m,n)`](@ref) is empty.)                                                                             |
| [`sparse(I,n,n)`](@ref)      | [`Matrix(I,n,n)`](@ref)  | Creates a *n*-by-*n* identity matrix.                                                                                                                |
| [`sparse(A)`](@ref)          | [`Array(S)`](@ref)       | Interconverts between dense and sparse formats.                                                                                                      |
| [`sprand(m,n,d)`](@ref)      | [`rand(m,n)`](@ref)      | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed uniformly on the half-open interval $[0, 1)$.             |
| [`sprandn(m,n,d)`](@ref)     | [`randn(m,n)`](@ref)     | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed according to the standard normal (Gaussian) distribution. |
| [`sprandn(rng,m,n,d)`](@ref) | [`randn(rng,m,n)`](@ref) | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements generated with the `rng` random number generator                      |

## [Sparse Linear Algebra](@id stdlib-sparse-linalg)

희소 행렬 솔버는 [SuiteSparse](http://suitesparse.com)에서 함수를 호출합니다. 다음과 같은 분해가 가능합니다:

| Type                | Description                      |
|:------------------- |:-------------------------------- |
| `CHOLMOD.Factor`    | Cholesky and LDLt factorizations |
| `UMFPACK.UmfpackLU` | LU factorization                 |
| `SPQR.QRSparse`     | QR factorization                 |

이러한 인수분해는 [Sparse Linear Algebra API section](@ref stdlib-sparse-linalg-api)에서 더 자세히 설명되어 있습니다:

1. [`cholesky`](@ref SparseArrays.CHOLMOD.cholesky)
2. [`ldlt`](@ref SparseArrays.CHOLMOD.ldlt)
3. [`lu`](@ref SparseArrays.UMFPACK.lu)
4. [`qr`](@ref SparseArrays.SPQR.qr)

```@meta
DocTestSetup = nothing
```

# [SparseArrays API](@id stdlib-sparse-arrays)

```@docs
SparseArrays.AbstractSparseArray
SparseArrays.AbstractSparseVector
SparseArrays.AbstractSparseMatrix
SparseArrays.SparseVector
SparseArrays.SparseMatrixCSC
SparseArrays.sparse
SparseArrays.sparse!
SparseArrays.sparsevec
Base.similar(::SparseArrays.AbstractSparseMatrixCSC, ::Type)
SparseArrays.issparse
SparseArrays.nnz
SparseArrays.findnz
SparseArrays.spzeros
SparseArrays.spzeros!
SparseArrays.spdiagm
SparseArrays.sparse_hcat
SparseArrays.sparse_vcat
SparseArrays.sparse_hvcat
SparseArrays.blockdiag
SparseArrays.sprand
SparseArrays.sprandn
SparseArrays.nonzeros
SparseArrays.rowvals
SparseArrays.nzrange
SparseArrays.droptol!
SparseArrays.dropzeros!
SparseArrays.dropzeros
SparseArrays.permute
permute!{Tv, Ti, Tp <: Integer, Tq <: Integer}(::SparseMatrixCSC{Tv,Ti}, ::SparseMatrixCSC{Tv,Ti}, ::AbstractArray{Tp,1}, ::AbstractArray{Tq,1})
SparseArrays.halfperm!
SparseArrays.ftranspose!
```

```@meta
DocTestSetup = nothing
```

# [Sparse Linear Algebra API](@id stdlib-sparse-linalg-api)

```@docs; canonical=false
SparseArrays.CHOLMOD.cholesky
SparseArrays.CHOLMOD.cholesky!
SparseArrays.CHOLMOD.lowrankupdate
SparseArrays.CHOLMOD.lowrankupdate!
SparseArrays.CHOLMOD.lowrankdowndate
SparseArrays.CHOLMOD.lowrankdowndate!
SparseArrays.CHOLMOD.lowrankupdowndate!
SparseArrays.CHOLMOD.ldlt
SparseArrays.UMFPACK.lu
SparseArrays.SPQR.qr
```

```@meta
DocTestSetup = nothing
```

# Noteworthy External Sparse Packages

여러 다른 Julia 패키지가 언급해야 할 희소 행렬 구현을 제공합니다:

1. [SuiteSparseGraphBLAS.jl](https://github.com/JuliaSparse/SuiteSparseGraphBLAS.jl)는 빠르고 다중 스레드 지원을 하는 SuiteSparse:GraphBLAS C 라이브러리에 대한 래퍼입니다. CPU에서 이는 일반적으로 가장 빠른 옵션으로, 종종 MKLSparse보다 상당히 뛰어난 성능을 발휘합니다.
2. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl)는 GPU 희소 행렬 연산을 위한 [CUSPARSE](https://docs.nvidia.com/cuda/cusparse/index.html) 라이브러리를 노출합니다.
3. [SparseMatricesCSR.jl](https://github.com/gridap/SparseMatricesCSR.jl)는 압축 희소 행렬(CSR) 형식의 Julia 네이티브 구현을 제공합니다.
4. [MKLSparse.jl](https://github.com/JuliaSparse/MKLSparse.jl)는 Intel의 MKL 라이브러리를 사용하여 SparseArrays의 희소-밀집 행렬 연산을 가속화합니다.
5. [SparseArrayKit.jl](https://github.com/Jutho/SparseArrayKit.jl) 다차원 희소 배열에 사용할 수 있습니다.
6. [LuxurySparse.jl](https://github.com/QuantumBFS/LuxurySparse.jl)는 정적 희소 배열 형식과 좌표 형식을 제공합니다.
7. [ExtendableSparse.jl](https://github.com/j-fu/ExtendableSparse.jl)는 새로운 저장된 인덱스에 대한 지연 접근 방식을 사용하여 희소 행렬에 빠른 삽입을 가능하게 합니다.
8. [Finch.jl](https://github.com/willow-ahrens/Finch.jl)는 미니 텐서 언어와 컴파일러를 통해 광범위한 다차원 희소 배열 형식 및 연산을 지원하며, 모두 네이티브 줄리아로 작성되었습니다. COO, CSF, CSR, CSC 등과 같은 형식과 브로드캐스트, 리듀스 등과 같은 연산 및 사용자 정의 연산을 지원합니다.

외부 패키지에서 제공하는 희소 직접 솔버:

1. [KLU.jl](https://github.com/JuliaSparse/KLU.jl)
2. [Pardiso.jl](https://github.com/JuliaSparse/Pardiso.jl/)

외부 패키지들은 고유 시스템과 특이값 분해의 반복적 해결을 위한 솔버를 제공합니다:

1. [ArnoldiMethods.jl](https://github.com/JuliaLinearAlgebra/ArnoldiMethod.jl)
2. [KrylovKit](https://github.com/Jutho/KrylovKit.jl)
3. [Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl)

그래프 작업을 위한 외부 패키지:

1. [Graphs.jl](https://github.com/JuliaGraphs/Graphs.jl)
