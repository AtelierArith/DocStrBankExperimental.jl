```
findnz(A::SparseMatrixCSC)
```

返回一个元组 `(I, J, V)`，其中 `I` 和 `J` 是稀疏矩阵 `A` 中存储的（“结构上非零”）值的行和列索引，`V` 是值的向量。

# 示例

```jldoctest
julia> A = sparse([1 2 0; 0 0 3; 0 4 0])
3×3 SparseMatrixCSC{Int64, Int64} with 4 stored entries:
 1  2  ⋅
 ⋅  ⋅  3
 ⋅  4  ⋅

julia> findnz(A)
([1, 1, 3, 2], [1, 2, 2, 3], [1, 2, 4, 3])
```
