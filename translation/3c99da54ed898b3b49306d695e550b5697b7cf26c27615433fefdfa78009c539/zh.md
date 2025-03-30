```
inv(M)
```

矩阵的逆。计算矩阵 `N` 使得 `M * N = I`，其中 `I` 是单位矩阵。通过求解左除 `N = M \ I` 来计算。

# 示例

```jldoctest
julia> M = [2 5; 1 3]
2×2 Matrix{Int64}:
 2  5
 1  3

julia> N = inv(M)
2×2 Matrix{Float64}:
  3.0  -5.0
 -1.0   2.0

julia> M*N == N*M == Matrix(I, 2, 2)
true
```
