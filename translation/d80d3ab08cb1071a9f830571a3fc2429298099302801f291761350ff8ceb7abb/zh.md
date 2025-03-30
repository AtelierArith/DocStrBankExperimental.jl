```
dropzeros(A::AbstractSparseMatrixCSC;)
```

生成 `A` 的副本，并从该副本中移除存储的数值零。

有关就地版本和算法信息，请参见 [`dropzeros!`](@ref)。

# 示例

```jldoctest
julia> A = sparse([1, 2, 3], [1, 2, 3], [1.0, 0.0, 1.0])
3×3 SparseMatrixCSC{Float64, Int64} 具有 3 个存储条目：
 1.0   ⋅    ⋅
  ⋅   0.0   ⋅
  ⋅    ⋅   1.0

julia> dropzeros(A)
3×3 SparseMatrixCSC{Float64, Int64} 具有 2 个存储条目：
 1.0   ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅   1.0
```
