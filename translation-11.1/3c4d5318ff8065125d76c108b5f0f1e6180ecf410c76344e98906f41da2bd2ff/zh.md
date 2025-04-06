```
argmax(itr)
```

返回集合中最大元素的索引或键。如果有多个最大元素，则返回第一个。

集合不能为空。

索引与[`keys(itr)`](@ref)和[`pairs(itr)`](@ref)返回的类型相同。

值通过`isless`进行比较。

另请参见：[`argmin`](@ref)，[`findmax`](@ref)。

# 示例

```jldoctest
julia> argmax([8, 0.1, -9, pi])
1

julia> argmax([1, 7, 7, 6])
2

julia> argmax([1, 7, 7, NaN])
4
```
