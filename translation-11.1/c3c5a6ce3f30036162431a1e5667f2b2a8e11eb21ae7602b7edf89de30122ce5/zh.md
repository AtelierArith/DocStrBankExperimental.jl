```
nonzeros(A)
```

返回稀疏数组 `A` 中结构非零值的向量。这包括在稀疏数组中显式存储的零。返回的向量直接指向 `A` 的内部非零存储，对返回向量的任何修改也会改变 `A`。请参见 [`rowvals`](@ref) 和 [`nzrange`](@ref)。

# 示例

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> nonzeros(A)
3-element Vector{Int64}:
 2
 2
 2
```
