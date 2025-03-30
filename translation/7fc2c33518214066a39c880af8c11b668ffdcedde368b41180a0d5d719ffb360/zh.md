```
mean(itr)
```

计算集合中所有元素的平均值。

!!! note
    如果 `itr` 包含 `NaN` 或 [`missing`](@ref) 值，结果也将是 `NaN` 或 `missing`（如果数组同时包含两者，则 `missing` 优先）。使用 [`skipmissing`](@ref) 函数来省略 `missing` 条目并计算非缺失值的平均值。


# 示例

```jldoctest
julia> using Statistics

julia> mean(1:20)
10.5

julia> mean([1, missing, 3])
missing

julia> mean(skipmissing([1, missing, 3]))
2.0
```
