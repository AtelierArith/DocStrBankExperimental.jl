```
eigvecs(A, B) -> 矩阵
```

返回一个矩阵 `M`，其列是 `A` 和 `B` 的广义特征向量。(`k`th 特征向量可以通过切片 `M[:, k]` 获得。)

# 示例

```jldoctest
julia> A = [1 0; 0 -1]
2×2 矩阵{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 矩阵{Int64}:
 0  1
 1  0

julia> eigvecs(A, B)
2×2 矩阵{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im
```
