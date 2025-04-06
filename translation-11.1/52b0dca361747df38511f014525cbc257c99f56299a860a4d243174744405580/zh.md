```
^(A::AbstractMatrix, p::Number)
```

矩阵幂，相当于 $\exp(p\log(A))$

# 示例

```jldoctest
julia> [1 2; 0 3]^3
2×2 Matrix{Int64}:
 1  26
 0  27
```
