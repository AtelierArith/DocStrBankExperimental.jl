```
invpermute!(v, p)
```

与 [`permute!`](@ref) 类似，但应用给定排列的逆排列。

请注意，如果您有一个预分配的输出数组（例如 `u = similar(v)`），那么使用 `u[p] = v` 会更快。 (`invpermute!` 在内部会分配数据的副本。)

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


# 示例

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> invpermute!(A, perm);

julia> A
4-element Vector{Int64}:
 4
 1
 3
 1
```
