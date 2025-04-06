```
spzeros([type,]m[,n])
```

创建一个长度为 `m` 的稀疏向量或大小为 `m x n` 的稀疏矩阵。该稀疏数组将不包含任何非零值。在构造过程中不会为非零值分配任何存储。如果未指定类型，则默认为 [`Float64`](@ref)。

# 示例

```jldoctest
julia> spzeros(3, 3)
3×3 SparseMatrixCSC{Float64, Int64} with 0 stored entries:
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅    ⋅

julia> spzeros(Float32, 4)
4-element SparseVector{Float32, Int64} with 0 stored entries
```
