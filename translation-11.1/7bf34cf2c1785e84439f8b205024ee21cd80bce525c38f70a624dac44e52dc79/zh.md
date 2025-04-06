```
lu(A, pivot = RowMaximum(); check = true, allowsingular = false) -> F::LU
```

计算 `A` 的 LU 分解。

当 `check = true` 时，如果分解失败，将抛出错误。当 `check = false` 时，检查分解有效性的责任（通过 [`issuccess`](@ref)）由用户承担。

默认情况下，当 `check = true` 时，如果分解产生有效因子，但上三角因子 `U` 的秩不足，也会抛出错误。可以通过传递 `allowsingular = true` 来更改此行为。

在大多数情况下，如果 `A` 是 `AbstractMatrix{T}` 的子类型 `S`，且元素类型 `T` 支持 `+`、`-`、`*` 和 `/`，则返回类型为 `LU{T,S{T}}`。

一般来说，LU 分解涉及对矩阵行的排列（对应于下面描述的 `F.p` 输出），称为“主元选择”（因为它对应于选择哪个行包含“主元”，即 `F.U` 的对角元素）。可以通过可选的 `pivot` 参数选择以下主元选择策略：

  * `RowMaximum()`（默认）：标准主元选择策略；主元对应于剩余待分解行中绝对值最大的元素。此主元选择策略要求元素类型也支持 [`abs`](@ref) 和 [`<`](@ref)。 （这通常是浮点矩阵的唯一数值稳定选项。）
  * `RowNonZero()`：主元对应于剩余待分解行中第一个非零元素。 （这对应于手动计算中的典型选择，对于支持 [`iszero`](@ref) 但不支持 `abs` 或 `<` 的更一般的代数数类型也很有用。）
  * `NoPivot()`：关闭主元选择（如果在主元位置遇到零条目，将失败，即使 `allowsingular = true`）。

可以通过 [`getproperty`](@ref) 访问分解 `F` 的各个组成部分：

| 组件    | 描述               |
|:----- |:---------------- |
| `F.L` | `L`（下三角）部分的 `LU` |
| `F.U` | `U`（上三角）部分的 `LU` |
| `F.p` | （右）排列 `Vector`   |
| `F.P` | （右）排列 `Matrix`   |

迭代分解会产生组件 `F.L`、`F.U` 和 `F.p`。

`F` 和 `A` 之间的关系是

`F.L*F.U == A[F.p, :]`

`F` 进一步支持以下函数：

| 支持的函数               | `LU` | `LU{T,Tridiagonal{T}}` |
|:------------------- |:---- |:---------------------- |
| [`/`](@ref)         | ✓    |                        |
| [`\`](@ref)         | ✓    | ✓                      |
| [`inv`](@ref)       | ✓    | ✓                      |
| [`det`](@ref)       | ✓    | ✓                      |
| [`logdet`](@ref)    | ✓    | ✓                      |
| [`logabsdet`](@ref) | ✓    | ✓                      |
| [`size`](@ref)      | ✓    | ✓                      |

!!! compat "Julia 1.11"
    `allowsingular` 关键字参数是在 Julia 1.11 中添加的。


# 示例

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U factor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # 通过迭代解构

julia> l == F.L && u == F.U && p == F.p
true

julia> lu([1 2; 1 2], allowsingular = true)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0  0.0
 1.0  1.0
U factor (rank-deficient):
2×2 Matrix{Float64}:
 1.0  2.0
 0.0  0.0
```
