```@meta
EditURL = "https://github.com/JuliaSparse/SparseArrays.jl/blob/master/docs/src/index.md"
```

# Sparse Arrays

```@meta
DocTestSetup = :(using SparseArrays, LinearAlgebra)
```

Julia 对稀疏向量和 [sparse matrices](https://en.wikipedia.org/wiki/Sparse_matrix) 在 `SparseArrays` 标准库模块中提供支持。稀疏数组是指包含足够多零的数组，将它们存储在特殊数据结构中可以节省空间和执行时间，相较于密集数组。

可以在 [Noteworthy External Sparse Packages](@ref) 中找到实现不同稀疏存储类型、多维稀疏数组等的外部包。

## [Compressed Sparse Column (CSC) Sparse Matrix Storage](@id man-csc)

在 Julia 中，稀疏矩阵存储在 [Compressed Sparse Column (CSC) format](https://en.wikipedia.org/wiki/Sparse_matrix#Compressed_sparse_column_.28CSC_or_CCS.29) 中。Julia 稀疏矩阵的类型为 [`SparseMatrixCSC{Tv,Ti}`](@ref)，其中 `Tv` 是存储值的类型，`Ti` 是用于存储列指针和行索引的整数类型。`SparseMatrixCSC` 的内部表示如下：

```julia
struct SparseMatrixCSC{Tv,Ti<:Integer} <: AbstractSparseMatrixCSC{Tv,Ti}
    m::Int                  # Number of rows
    n::Int                  # Number of columns
    colptr::Vector{Ti}      # Column j is in colptr[j]:(colptr[j+1]-1)
    rowval::Vector{Ti}      # Row indices of stored values
    nzval::Vector{Tv}       # Stored values, typically nonzeros
end
```

压缩稀疏列存储使得访问稀疏矩阵列中的元素变得简单快捷，而按行访问稀疏矩阵则明显较慢。在CSC结构中，逐个插入之前未存储的条目等操作往往较慢。这是因为所有在插入点之后的稀疏矩阵元素都必须向后移动一个位置。

所有对稀疏矩阵的操作都经过精心实现，以利用CSC数据结构提高性能，并避免昂贵的操作。

如果您有来自不同应用程序或库的 CSC 格式数据，并希望在 Julia 中导入，请确保使用 1 基索引。每列中的行索引需要排序，如果没有排序，矩阵将显示不正确。如果您的 `SparseMatrixCSC` 对象包含未排序的行索引，一种快速的排序方法是进行双重转置。由于转置操作是惰性执行的，请复制以实现每次转置的具体化。

在某些应用中，将显式零值存储在 `SparseMatrixCSC` 中是方便的。这些 *是* 被 `Base` 中的函数接受的（但不能保证在变更操作中会被保留）。许多例程将这些显式存储的零视为结构非零。[`nnz`](@ref) 函数返回稀疏数据结构中显式存储的元素数量，包括非结构零。为了准确计算数值非零的数量，请使用 [`count(!iszero, x)`](@ref)，该函数检查稀疏矩阵中每个存储的元素。[`dropzeros`](@ref) 和就地的 [`dropzeros!`](@ref) 可用于从稀疏矩阵中移除存储的零。

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

稀疏向量以与稀疏矩阵的压缩稀疏列格式相似的方式存储。在 Julia 中，稀疏向量的类型为 [`SparseVector{Tv,Ti}`](@ref)，其中 `Tv` 是存储值的类型，`Ti` 是索引的整数类型。内部表示如下：

```julia
struct SparseVector{Tv,Ti<:Integer} <: AbstractSparseVector{Tv,Ti}
    n::Int              # Length of the sparse vector
    nzind::Vector{Ti}   # Indices of stored values
    nzval::Vector{Tv}   # Stored values, typically nonzeros
end
```

关于 [`SparseMatrixCSC`](@ref)，`SparseVector` 类型也可以包含显式存储的零。（参见 [Sparse Matrix Storage](@ref man-csc)。）

## Sparse Vector and Matrix Constructors

创建稀疏数组的最简单方法是使用一个等同于 [`zeros`](@ref) 的函数，该函数是 Julia 提供的用于处理密集数组的函数。要生成稀疏数组，您可以使用相同的名称并加上 `sp` 前缀：

```jldoctest
julia> spzeros(3)
3-element SparseVector{Float64, Int64} with 0 stored entries
```

[`sparse`](@ref) 函数通常是构造稀疏数组的便捷方法。例如，要构造一个稀疏矩阵，我们可以输入一个行索引向量 `I`、一个列索引向量 `J` 和一个存储值的向量 `V`（这也被称为 [COO (coordinate) format](https://en.wikipedia.org/wiki/Sparse_matrix#Coordinate_list_.28COO.29)）。然后，`sparse(I,J,V)` 构造一个稀疏矩阵，使得 `S[I[k], J[k]] = V[k]`。等效的稀疏向量构造函数是 [`sparsevec`](@ref)，它接受（行）索引向量 `I` 和存储值的向量 `V`，并构造一个稀疏向量 `R`，使得 `R[I[k]] = V[k]`。

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

[`sparse`](@ref) 和 [`sparsevec`](@ref) 函数的逆是 [`findnz`](@ref)，它检索用于创建稀疏数组的输入（包括等于零的存储条目）。 [`findall(!iszero, x)`](@ref) 返回 `x` 中非零条目的笛卡尔索引（不包括等于零的存储条目）。

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

另一种创建稀疏数组的方法是使用 [`sparse`](@ref) 函数将密集数组转换为稀疏数组：

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

您可以使用 [`Array`](@ref) 构造函数朝另一个方向前进。[`issparse`](@ref) 函数可用于查询矩阵是否稀疏。

```jldoctest
julia> issparse(spzeros(5))
true
```

## Sparse matrix operations

稀疏矩阵上的算术运算与密集矩阵上的运算相同。稀疏矩阵的索引、赋值和连接的方式与密集矩阵相同。索引操作，特别是赋值，在逐个元素执行时是昂贵的。在许多情况下，将稀疏矩阵转换为 `(I,J,V)` 格式可能更好，使用 [`findnz`](@ref)，在密集向量 `(I,J,V)` 中操作值或结构，然后重建稀疏矩阵。

## Correspondence of dense and sparse methods

下表给出了稀疏矩阵上的内置方法与其对应的密集矩阵类型的方法之间的对应关系。一般来说，生成稀疏矩阵的方法与其密集对应物的不同之处在于，生成的矩阵遵循给定稀疏矩阵 `S` 的相同稀疏模式，或者生成的稀疏矩阵具有密度 `d`，即每个矩阵元素有概率 `d` 为非零。

详细信息可以在标准库参考的 [Sparse Vectors and Matrices](@ref stdlib-sparse-arrays) 部分找到。

| Sparse                       | Dense                    | Description                                                                                                                                          |
|:---------------------------- |:------------------------ |:---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`spzeros(m,n)`](@ref)       | [`zeros(m,n)`](@ref)     | Creates a *m*-by-*n* matrix of zeros. ([`spzeros(m,n)`](@ref) is empty.)                                                                             |
| [`sparse(I,n,n)`](@ref)      | [`Matrix(I,n,n)`](@ref)  | Creates a *n*-by-*n* identity matrix.                                                                                                                |
| [`sparse(A)`](@ref)          | [`Array(S)`](@ref)       | Interconverts between dense and sparse formats.                                                                                                      |
| [`sprand(m,n,d)`](@ref)      | [`rand(m,n)`](@ref)      | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed uniformly on the half-open interval $[0, 1)$.             |
| [`sprandn(m,n,d)`](@ref)     | [`randn(m,n)`](@ref)     | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements distributed according to the standard normal (Gaussian) distribution. |
| [`sprandn(rng,m,n,d)`](@ref) | [`randn(rng,m,n)`](@ref) | Creates a *m*-by-*n* random matrix (of density *d*) with iid non-zero elements generated with the `rng` random number generator                      |

## [Sparse Linear Algebra](@id stdlib-sparse-linalg)

稀疏矩阵求解器调用来自 [SuiteSparse](http://suitesparse.com) 的函数。以下分解可用：

| Type                | Description                      |
|:------------------- |:-------------------------------- |
| `CHOLMOD.Factor`    | Cholesky and LDLt factorizations |
| `UMFPACK.UmfpackLU` | LU factorization                 |
| `SPQR.QRSparse`     | QR factorization                 |

这些因式分解在 [Sparse Linear Algebra API section](@ref stdlib-sparse-linalg-api) 中有更详细的描述：

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

几个其他的 Julia 包提供了稀疏矩阵的实现，值得一提：

1. [SuiteSparseGraphBLAS.jl](https://github.com/JuliaSparse/SuiteSparseGraphBLAS.jl) 是一个快速的多线程 SuiteSparse:GraphBLAS C 库的封装。在 CPU 上，这通常是最快的选项，通常显著优于 MKLSparse。
2. [CUDA.jl](https://github.com/JuliaGPU/CUDA.jl) 暴露了 [CUSPARSE](https://docs.nvidia.com/cuda/cusparse/index.html) 库，用于 GPU 稀疏矩阵操作。
3. [SparseMatricesCSR.jl](https://github.com/gridap/SparseMatricesCSR.jl) 提供了一个 Julia 原生实现的压缩稀疏行 (CSR) 格式。
4. [MKLSparse.jl](https://github.com/JuliaSparse/MKLSparse.jl) 加速了 SparseArrays 稀疏-密集矩阵操作，使用了英特尔的 MKL 库。
5. [SparseArrayKit.jl](https://github.com/Jutho/SparseArrayKit.jl) 可用于多维稀疏数组。
6. [LuxurySparse.jl](https://github.com/QuantumBFS/LuxurySparse.jl) 提供静态稀疏数组格式以及坐标格式。
7. [ExtendableSparse.jl](https://github.com/j-fu/ExtendableSparse.jl) 通过对新存储索引的懒惰方法实现了对稀疏矩阵的快速插入。
8. [Finch.jl](https://github.com/willow-ahrens/Finch.jl) 支持通过迷你张量语言和编译器进行广泛的多维稀疏数组格式和操作，全部使用原生 Julia。支持 COO、CSF、CSR、CSC 等格式，以及广播、归约等操作和自定义操作。

外部包提供稀疏直接求解器：

1. [KLU.jl](https://github.com/JuliaSparse/KLU.jl)
2. [Pardiso.jl](https://github.com/JuliaSparse/Pardiso.jl/)

外部包提供用于特征系统和奇异值分解的迭代解法的求解器：

1. [ArnoldiMethods.jl](https://github.com/JuliaLinearAlgebra/ArnoldiMethod.jl)
2. [KrylovKit](https://github.com/Jutho/KrylovKit.jl)
3. [Arpack.jl](https://github.com/JuliaLinearAlgebra/Arpack.jl)

用于处理图形的外部包：

1. [Graphs.jl](https://github.com/JuliaGraphs/Graphs.jl)
