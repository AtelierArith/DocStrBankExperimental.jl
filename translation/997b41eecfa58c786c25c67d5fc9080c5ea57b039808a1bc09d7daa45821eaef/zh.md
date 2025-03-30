```
setdiff(s, itrs...)
```

构造集合 `s` 中的元素，但不包括 `itrs` 中的任何可迭代对象。使用数组保持顺序。

另见 [`setdiff!`](@ref), [`union`](@ref) 和 [`intersect`](@ref)。

# 示例

```jldoctest
julia> setdiff([1,2,3], [3,4,5])
2-element Vector{Int64}:
 1
 2
```
