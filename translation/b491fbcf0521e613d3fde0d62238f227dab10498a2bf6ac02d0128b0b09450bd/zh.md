```
logdet(M)
```

矩阵行列式的对数。等同于 `log(det(M))`，但可能提供更高的精度，并避免溢出/下溢。

# 示例

```jldoctest
julia> M = [1 0; 2 2]
2×2 Matrix{Int64}:
 1  0
 2  2

julia> logdet(M)
0.6931471805599453

julia> logdet(Matrix(I, 3, 3))
0.0
```
