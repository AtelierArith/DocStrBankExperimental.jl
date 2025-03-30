```
prepend!(a::Vector, collections...) -> collection
```

将每个 `collections` 的元素插入到 `a` 的开头。

当 `collections` 指定多个集合时，顺序保持不变：`collections[1]` 的元素将最左侧出现在 `a` 中，依此类推。

!!! compat "Julia 1.6"
    指定多个集合以进行前置插入需要至少 Julia 1.6。


# 示例

```jldoctest
julia> prepend!([3], [1, 2])
3-element Vector{Int64}:
 1
 2
 3

julia> prepend!([6], [1, 2], [3, 4, 5])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
