```
LDLt <: Factorization
```

`LDLt` 分解的矩阵分解类型，适用于实数 [`SymTridiagonal`](@ref) 矩阵 `S`，使得 `S = L*Diagonal(d)*L'`，其中 `L` 是一个 [`UnitLowerTriangular`](@ref) 矩阵，`d` 是一个向量。`LDLt` 分解 `F = ldlt(S)` 的主要用途是求解线性方程组 `Sx = b`，使用 `F\b`。这是 [`ldlt`](@ref) 的返回类型，对应的矩阵分解函数。

可以通过 `getproperty` 访问分解 `F::LDLt` 的各个组成部分：

|   组件   | 描述                    |
|:------:|:--------------------- |
| `F.L`  | `L`（单位下三角）部分的 `LDLt`  |
| `F.D`  | `D`（对角）部分的 `LDLt`     |
| `F.Lt` | `Lt`（单位上三角）部分的 `LDLt` |
| `F.d`  | `D` 的对角值作为 `Vector`   |

# 示例

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> F = ldlt(S)
LDLt{Float64, SymTridiagonal{Float64, Vector{Float64}}}
L factor:
3×3 UnitLowerTriangular{Float64, SymTridiagonal{Float64, Vector{Float64}}}:
 1.0        ⋅         ⋅
 0.333333  1.0        ⋅
 0.0       0.545455  1.0
D factor:
3×3 Diagonal{Float64, Vector{Float64}}:
 3.0   ⋅        ⋅
  ⋅   3.66667   ⋅
  ⋅    ⋅       3.90909
```
