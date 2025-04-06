```
stdm(itr, mean; corrected::Bool=true[, dims])
```

计算集合 `itr` 的样本标准差，已知均值 `mean`。

该算法在假设 `itr` 的每个条目都是从同一未知分布中抽取的样本且样本不相关的情况下，返回生成分布的标准差的估计值。对于数组，这个计算等同于计算 `sqrt(sum((itr .- mean(itr)).^2) / (length(itr) - 1))`。如果 `corrected` 为 `true`，则总和按 `n-1` 进行缩放，而如果 `corrected` 为 `false`，则总和按 `n` 进行缩放，其中 `n` 是 `itr` 中元素的数量。

如果 `itr` 是 `AbstractArray`，可以提供 `dims` 来计算各维度的标准差。在这种情况下，`mean` 必须是与 `mean(itr, dims=dims)` 形状相同的数组（允许额外的尾随单例维度）。

!!! note
    如果数组包含 `NaN` 或 [`missing`](@ref) 值，则结果也为 `NaN` 或 `missing`（如果数组同时包含两者，则 `missing` 优先）。使用 [`skipmissing`](@ref) 函数来省略 `missing` 条目并计算非缺失值的标准差。

