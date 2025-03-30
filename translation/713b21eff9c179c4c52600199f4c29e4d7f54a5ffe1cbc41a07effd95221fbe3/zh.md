```
A / B
```

矩阵右除法：`A / B` 等价于 `(B' \ A')'`，其中 [`\`](@ref) 是左除法运算符。对于方阵，结果 `X` 满足 `A == X*B`。

另见：[`rdiv!`](@ref)。

# 示例

```jldoctest
julia> A = Float64[1 4 5; 3 9 2]; B = Float64[1 4 2; 3 4 2; 8 7 1];

julia> X = A / B
2×3 Matrix{Float64}:
 -0.65   3.75  -1.2
  3.25  -2.75   1.0

julia> isapprox(A, X*B)
true

julia> isapprox(X, A*pinv(B))
true
```
