```
issorted(v, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

测试一个集合是否按排序顺序排列。关键字修改被视为已排序的顺序，如 [`sort!`](@ref) 文档中所述。

# 示例

```jldoctest
julia> issorted([1, 2, 3])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[1])
true

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2])
false

julia> issorted([(1, "b"), (2, "a")], by = x -> x[2], rev=true)
true

julia> issorted([1, 2, -2, 3], by=abs)
true
```
