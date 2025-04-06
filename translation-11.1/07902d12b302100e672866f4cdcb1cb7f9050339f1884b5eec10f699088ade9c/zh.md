```
findmin(itr) -> (x, index)
```

返回集合 `itr` 的最小元素及其索引或键。如果有多个最小元素，则返回第一个。`NaN` 被视为小于所有其他值，除了 `missing`。

索引与 [`keys(itr)`](@ref) 和 [`pairs(itr)`](@ref) 返回的类型相同。

另请参见: [`findmax`](@ref), [`argmin`](@ref), [`minimum`](@ref).

# 示例

```jldoctest
julia> findmin([8, 0.1, -9, pi])
(-9.0, 3)

julia> findmin([1, 7, 7, 6])
(1, 1)

julia> findmin([1, 7, 7, NaN])
(NaN, 4)
```
