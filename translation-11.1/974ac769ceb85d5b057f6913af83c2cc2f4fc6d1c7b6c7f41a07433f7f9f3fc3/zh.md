```
median(itr)
```

计算集合中所有元素的中位数。对于偶数个元素，不存在确切的中位数元素，因此结果相当于计算两个中位数元素的平均值。

!!! note
    如果 `itr` 包含 `NaN` 或 [`missing`](@ref) 值，结果也将是 `NaN` 或 `missing`（如果 `itr` 同时包含两者，则 `missing` 优先）。使用 [`skipmissing`](@ref) 函数来省略 `missing` 条目并计算非缺失值的中位数。


# 示例

```jldoctest
julia> using Statistics

julia> median([1, 2, 3])
2.0

julia> median([1, 2, 3, 4])
2.5

julia> median([1, 2, missing, 4])
missing

julia> median(skipmissing([1, 2, missing, 4]))
2.0
```
