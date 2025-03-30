```
spdiagm(kv::Pair{<:Integer,<:AbstractVector}...)
spdiagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)
```

从 `Pair` 的向量和对角线构造稀疏对角矩阵。每个向量 `kv.second` 将放置在 `kv.first` 对角线上。默认情况下，矩阵是方形的，其大小由 `kv` 推断，但可以通过将 `m,n` 作为第一个参数传递来指定非方形大小 `m`×`n`（根据需要用零填充）。

# 示例

```jldoctest
julia> spdiagm(-1 => [1,2,3,4], 1 => [4,3,2,1])
5×5 SparseMatrixCSC{Int64, Int64} with 8 stored entries:
 ⋅  4  ⋅  ⋅  ⋅
 1  ⋅  3  ⋅  ⋅
 ⋅  2  ⋅  2  ⋅
 ⋅  ⋅  3  ⋅  1
 ⋅  ⋅  ⋅  4  ⋅
```
