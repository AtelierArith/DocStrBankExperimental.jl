```
qr(A, pivot = NoPivot(); blocksize) -> F
```

计算矩阵 `A` 的 QR 分解：一个正交（或如果 `A` 是复值则为单位）矩阵 `Q`，以及一个上三角矩阵 `R`，使得

$$
A = Q R
$$

返回的对象 `F` 以打包格式存储分解：

  * 如果 `pivot == ColumnNorm()`，则 `F` 是一个 [`QRPivoted`](@ref) 对象，
  * 否则如果 `A` 的元素类型是 BLAS 类型（[`Float32`](@ref)，[`Float64`](@ref)，`ComplexF32` 或 `ComplexF64`），则 `F` 是一个 [`QRCompactWY`](@ref) 对象，
  * 否则 `F` 是一个 [`QR`](@ref) 对象。

可以通过属性访问器检索分解 `F` 的各个组成部分：

  * `F.Q`：正交/单位矩阵 `Q`
  * `F.R`：上三角矩阵 `R`
  * `F.p`：置换向量（仅 [`QRPivoted`](@ref)）
  * `F.P`：置换矩阵（仅 [`QRPivoted`](@ref)）

!!! note
    每次通过 `F.R` 引用上三角因子都会分配一个新数组。因此，建议缓存该数组，例如，通过 `R = F.R` 并继续使用 `R`。


迭代分解会产生组件 `Q`、`R`，以及如果存在则为 `p`。

以下函数可用于 `QR` 对象：[`inv`](@ref)、[`size`](@ref) 和 [`\`](@ref)。当 `A` 是矩形时，`\` 将返回一个最小二乘解，如果解不是唯一的，则返回范数最小的解。当 `A` 不是满秩时，需要进行（列）置换的分解以获得最小范数解。

允许与全/方形或非全/方形 `Q` 进行乘法，即支持 `F.Q*F.R` 和 `F.Q*A`。可以使用 [`Matrix`](@ref) 将 `Q` 矩阵转换为常规矩阵。此操作返回“薄” Q 因子，即，如果 `A` 是 `m`×`n` 且 `m>=n`，则 `Matrix(F.Q)` 产生一个具有正交列的 `m`×`n` 矩阵。要检索“完整” Q 因子，即一个 `m`×`m` 的正交矩阵，请使用 `F.Q*I` 或 `collect(F.Q)`。如果 `m<=n`，则 `Matrix(F.Q)` 产生一个 `m`×`m` 的正交矩阵。

QR 分解的块大小可以通过关键字参数 `blocksize :: Integer` 指定，当 `pivot == NoPivot()` 且 `A isa StridedMatrix{<:BlasFloat}` 时。如果 `blocksize > minimum(size(A))`，则会被忽略。请参见 [`QRCompactWY`](@ref)。

!!! compat "Julia 1.4"
    `blocksize` 关键字参数需要 Julia 1.4 或更高版本。


# 示例

```jldoctest
julia> A = [3.0 -6.0; 4.0 -8.0; 0.0 1.0]
3×2 Matrix{Float64}:
 3.0  -6.0
 4.0  -8.0
 0.0   1.0

julia> F = qr(A)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q 因子：3×3 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R 因子：
2×2 Matrix{Float64}:
 -5.0  10.0
  0.0  -1.0

julia> F.Q * F.R == A
true
```

!!! note
    `qr` 返回多种类型，因为 LAPACK 使用几种表示法来最小化 Householder 基本反射器的乘积的内存存储需求，以便 `Q` 和 `R` 矩阵可以紧凑地存储，而不是作为两个单独的密集矩阵。

