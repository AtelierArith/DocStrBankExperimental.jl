```
argmin(itr)
```

返回集合中最小元素的索引或键。如果有多个最小元素，则返回第一个。

集合不能为空。

索引与[`keys(itr)`](@ref)和[`pairs(itr)`](@ref)返回的类型相同。

`NaN`被视为小于所有其他值，除了`missing`。

另请参见：[`argmax`](@ref)，[`findmin`](@ref)。

# 示例

```jldoctest
julia> argmin([8, 0.1, -9, pi])
3

julia> argmin([7, 1, 1, 6])
2

julia> argmin([7, 1, 1, NaN])
4
```
