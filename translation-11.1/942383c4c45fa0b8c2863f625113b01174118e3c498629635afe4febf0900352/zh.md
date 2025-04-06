```
LU <: Factorization
```

矩阵分解类型的 `LU` 分解一个方阵 `A`。这是 [`lu`](@ref) 的返回类型，对应的矩阵分解函数。

可以通过 [`getproperty`](@ref) 访问分解 `F::LU` 的各个组成部分：

| 组件    | 描述                 |
|:----- |:------------------ |
| `F.L` | `L`（单位下三角）部分的 `LU` |
| `F.U` | `U`（上三角）部分的 `LU`   |
| `F.p` | （右）置换 `Vector`     |
| `F.P` | （右）置换 `Matrix`     |

迭代分解会产生组件 `F.L`、`F.U` 和 `F.p`。

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
```
