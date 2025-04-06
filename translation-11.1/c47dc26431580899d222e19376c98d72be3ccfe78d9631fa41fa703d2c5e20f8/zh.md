```
first(itr, n::Integer)
```

获取可迭代集合 `itr` 的前 `n` 个元素，如果 `itr` 不够长，则返回更少的元素。

另见: [`startswith`](@ref), [`Iterators.take`](@ref).

!!! compat "Julia 1.6"
    此方法需要至少 Julia 1.6。


# 示例

```jldoctest
julia> first(["foo", "bar", "qux"], 2)
2-element Vector{String}:
 "foo"
 "bar"

julia> first(1:6, 10)
1:6

julia> first(Bool[], 1)
Bool[]
```
