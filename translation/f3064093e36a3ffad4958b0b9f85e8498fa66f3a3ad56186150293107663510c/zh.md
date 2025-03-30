```
sortperm!(ix, A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

与 [`sortperm`](@ref) 类似，但接受一个预分配的索引向量或数组 `ix`，其 `axes` 与 `A` 相同。`ix` 被初始化为包含 `LinearIndices(A)` 的值。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


!!! compat "Julia 1.9"
    接受 `dims` 的方法需要至少 Julia 1.9。


# 示例

```jldoctest
julia> v = [3, 1, 2]; p = zeros(Int, 3);

julia> sortperm!(p, v); p
3-element Vector{Int64}:
 2
 3
 1

julia> v[p]
3-element Vector{Int64}:
 1
 2
 3

julia> A = [8 7; 5 6]; p = zeros(Int,2, 2);

julia> sortperm!(p, A; dims=1); p
2×2 Matrix{Int64}:
 2  4
 1  3

julia> sortperm!(p, A; dims=2); p
2×2 Matrix{Int64}:
 3  1
 2  4
```
