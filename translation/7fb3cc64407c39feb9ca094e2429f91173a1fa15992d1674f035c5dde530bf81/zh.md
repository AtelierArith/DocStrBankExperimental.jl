```
findmax(itr) -> (x, index)
```

返回集合 `itr` 的最大元素及其索引或键。如果有多个最大元素，则返回第一个。值的比较使用 `isless`。

索引与 [`keys(itr)`](@ref) 和 [`pairs(itr)`](@ref) 返回的类型相同。

另请参见: [`findmin`](@ref), [`argmax`](@ref), [`maximum`](@ref)。

# 示例

```jldoctest
julia> findmax([8, 0.1, -9, pi])
(8.0, 1)

julia> findmax([1, 7, 7, 6])
(7, 2)

julia> findmax([1, 7, 7, NaN])
(NaN, 4)
```
