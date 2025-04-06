```
deleteat!(a::Vector, inds)
```

删除由 `inds` 给出的索引处的项，并返回修改后的 `a`。后续项会被移动以填补产生的空缺。

`inds` 可以是一个迭代器或一个已排序且唯一的整数索引集合，或者是与 `a` 长度相同的布尔向量，其中 `true` 表示要删除的条目。

# 示例

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], [true, false, true, false, true, false])
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], (2, 2))
ERROR: ArgumentError: indices must be unique and sorted
Stacktrace:
[...]
```
