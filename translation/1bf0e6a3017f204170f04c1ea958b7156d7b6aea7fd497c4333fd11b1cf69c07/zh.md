```
spdiagm(v::AbstractVector)
spdiagm(m::Integer, n::Integer, v::AbstractVector)
```

构造一个稀疏矩阵，其元素为向量的对角元素。默认情况下（未给定 `m` 和 `n`），矩阵为方形，其大小由 `length(v)` 给出，但可以通过将 `m` 和 `n` 作为第一个参数传递来指定非方形大小 `m`×`n`。

!!! compat "Julia 1.6"
    这些函数至少需要 Julia 1.6。


# 示例

```jldoctest
julia> spdiagm([1,2,3])
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3

julia> spdiagm(sparse([1,0,3]))
3×3 SparseMatrixCSC{Int64, Int64} with 2 stored entries:
 1  ⋅  ⋅
 ⋅  ⋅  ⋅
 ⋅  ⋅  3
```
