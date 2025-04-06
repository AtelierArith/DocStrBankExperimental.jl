```
ldlt(S::SymTridiagonal) -> LDLt
```

计算实对称三对角矩阵 `S` 的 `LDLt`（即 $LDL^T$）分解，使得 `S = L*Diagonal(d)*L'`，其中 `L` 是单位下三角矩阵，`d` 是一个向量。`LDLt` 分解 `F = ldlt(S)` 的主要用途是求解线性方程组 `Sx = b`，使用 `F\b`。

另请参见 [`bunchkaufman`](@ref)，它是任意对称或厄米矩阵的类似但带有主元的分解。

# 示例

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> ldltS = ldlt(S);

julia> b = [6., 7., 8.];

julia> ldltS \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255

julia> S \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255
```
