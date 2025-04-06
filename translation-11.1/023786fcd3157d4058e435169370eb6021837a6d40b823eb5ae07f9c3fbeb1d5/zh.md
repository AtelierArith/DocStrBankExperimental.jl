```
^(b::Number, A::AbstractMatrix)
```

矩阵指数，等价于 $\exp(\log(b)A)$。

!!! compat "Julia 1.1"
    在 Julia 1.1 中添加了对将 `Irrational` 数字（如 `ℯ`）提升到矩阵的支持。


# 示例

```jldoctest
julia> 2^[1 2; 0 3]
2×2 Matrix{Float64}:
 2.0  6.0
 0.0  8.0

julia> ℯ^[1 2; 0 3]
2×2 Matrix{Float64}:
 2.71828  17.3673
 0.0      20.0855
```
