```
permute!(v, p)
```

就地对向量 `v` 进行置换，按照置换 `p`。不会检查 `p` 是否为一个置换。

要返回一个新的置换，请使用 `v[p]`。这通常比 `permute!(v, p)` 更快；使用 `u .= @view v[p]` 写入预分配的输出数组甚至更快。（尽管 `permute!` 就地覆盖 `v`，但它在内部需要一些分配来跟踪哪些元素已被移动。）

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


另请参见 [`invpermute!`](@ref)。

# 示例

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> permute!(A, perm);

julia> A
4-element Vector{Int64}:
 1
 4
 3
 1
```
