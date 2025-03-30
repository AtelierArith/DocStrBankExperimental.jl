```
first(coll)
```

获取可迭代集合的第一个元素。即使是空的，也会返回[`AbstractRange`](@ref)的起始点。

另见：[`only`](@ref)，[`firstindex`](@ref)，[`last`](@ref)。

# 示例

```jldoctest
julia> first(2:2:10)
2

julia> first([1; 2; 3; 4])
1
```
