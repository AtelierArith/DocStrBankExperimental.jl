```
sparse(I, J, V,[ m, n, combine])
```

创建一个维度为 `m x n` 的稀疏矩阵 `S`，使得 `S[I[k], J[k]] = V[k]`。`combine` 函数用于合并重复项。如果未指定 `m` 和 `n`，则它们分别设置为 `maximum(I)` 和 `maximum(J)`。如果未提供 `combine` 函数，则 `combine` 默认为 `+`，除非 `V` 的元素为布尔值，此时 `combine` 默认为 `|`。所有的 `I` 元素必须满足 `1 <= I[k] <= m`，所有的 `J` 元素必须满足 `1 <= J[k] <= n`。在 (`I`, `J`, `V`) 中的数值零被保留为结构非零；要删除数值零，请使用 [`dropzeros!`](@ref)。

有关更多文档和专家驱动程序，请参见 `SparseArrays.sparse!`。

# 示例

```jldoctest
julia> Is = [1; 2; 3];

julia> Js = [1; 2; 3];

julia> Vs = [1; 2; 3];

julia> sparse(Is, Js, Vs)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3
```
