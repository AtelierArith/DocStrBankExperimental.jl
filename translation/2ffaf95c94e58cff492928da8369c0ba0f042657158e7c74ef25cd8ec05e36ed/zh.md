```
对角线(A::AbstractMatrix)
```

从 `A` 的主对角线构造一个矩阵。输入矩阵 `A` 可以是矩形的，但输出将是方形的。

# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> D = Diagonal(A)
2×2 Diagonal{Int64, Vector{Int64}}:
 1  ⋅
 ⋅  4

julia> A = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> Diagonal(A)
2×2 Diagonal{Int64, Vector{Int64}}:
 1  ⋅
 ⋅  5
```
