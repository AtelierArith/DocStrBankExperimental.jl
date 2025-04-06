```
LinearAlgebra.checksquare(A)
```

检查一个矩阵是否为方阵，然后返回其公共维度。对于多个参数，返回一个向量。

# 示例

```jldoctest
julia> A = fill(1, (4,4)); B = fill(1, (5,5));

julia> LinearAlgebra.checksquare(A, B)
2-element Vector{Int64}:
 4
 5
```
