```
rowvals(A::AbstractSparseMatrixCSC)
```

返回 `A` 的行索引向量。对返回的向量的任何修改也会改变 `A`。提供对行索引内部存储方式的访问在与遍历结构非零值时可能会很有用。另请参见 [`nonzeros`](@ref) 和 [`nzrange`](@ref)。

# 示例

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> rowvals(A)
3-element Vector{Int64}:
 1
 2
 3
```
