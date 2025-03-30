```
partialsortperm!(ix, v, k; by=identity, lt=isless, rev=false)
```

类似于 [`partialsortperm`](@ref)，但接受一个与 `v` 大小相同的预分配索引向量 `ix`，该向量用于存储 `v` 的索引（的一个排列）。

`ix` 被初始化为包含 `v` 的索引。

（通常，`v` 的索引将是 `1:length(v)`，尽管如果 `v` 具有非一基索引的替代数组类型，例如 `OffsetArray`，则 `ix` 必须共享这些相同的索引）

返回时，`ix` 保证在其排序位置中具有索引 `k`，使得

```julia
partialsortperm!(ix, v, k);
v[ix[k]] == partialsort(v, k)
```

返回值是 `ix` 的第 `k` 个元素，如果 `k` 是一个整数，或者是 `ix` 的视图，如果 `k` 是一个范围。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


# 示例

```jldoctest
julia> v = [3, 1, 2, 1];

julia> ix = Vector{Int}(undef, 4);

julia> partialsortperm!(ix, v, 1)
2

julia> ix = [1:4;];

julia> partialsortperm!(ix, v, 2:3)
2-element view(::Vector{Int64}, 2:3) with eltype Int64:
 4
 3
```

```
