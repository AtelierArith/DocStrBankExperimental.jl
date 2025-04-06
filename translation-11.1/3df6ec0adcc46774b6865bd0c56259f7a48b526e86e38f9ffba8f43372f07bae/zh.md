```
quantile(itr, p; sorted=false, alpha::Real=1.0, beta::Real=alpha)
```

计算集合 `itr` 在指定概率或概率向量或元组 `p` 上的分位数，范围为 [0,1]。关键字参数 `sorted` 表示是否可以假设 `itr` 已经排序。

样本分位数由 `Q(p) = (1-γ)*x[j] + γ*x[j+1]` 定义，其中 `x[j]` 是 `itr` 的第 j 个顺序统计量，`j = floor(n*p + m)`，`m = alpha + p*(1 - alpha - beta)`，`γ = n*p + m - j`。

默认情况下（`alpha = beta = 1`），分位数通过在点 `((k-1)/(n-1), x[k])` 之间进行线性插值计算，其中 `k = 1:n`，`n = length(itr)`。这对应于 Hyndman 和 Fan (1996) 的定义 7，并且与 R 和 NumPy 的默认值相同。

关键字参数 `alpha` 和 `beta` 对应于 Hyndman 和 Fan 中的相同参数，将它们设置为不同的值可以使用本文中定义的 4-9 方法计算分位数：

  * 定义 4: `alpha=0`，`beta=1`
  * 定义 5: `alpha=0.5`，`beta=0.5`（MATLAB 默认）
  * 定义 6: `alpha=0`，`beta=0`（Excel `PERCENTILE.EXC`，Python 默认，Stata `altdef`）
  * 定义 7: `alpha=1`，`beta=1`（Julia、R 和 NumPy 默认，Excel `PERCENTILE` 和 `PERCENTILE.INC`，Python `'inclusive'`）
  * 定义 8: `alpha=1/3`，`beta=1/3`
  * 定义 9: `alpha=3/8`，`beta=3/8`

!!! note
    如果 `v` 包含 `NaN` 或 [`missing`](@ref) 值，将抛出 `ArgumentError`。使用 [`skipmissing`](@ref) 函数来省略 `missing` 条目并计算非缺失值的分位数。


# 参考文献

  * Hyndman, R.J 和 Fan, Y. (1996) "统计软件中的样本分位数", *美国统计学家*, 第 50 卷，第 4 期，页 361-365
  * [维基百科上的分位数](https://en.m.wikipedia.org/wiki/Quantile) 详细介绍了不同的分位数定义

# 示例

```jldoctest
julia> using Statistics

julia> quantile(0:20, 0.5)
10.0

julia> quantile(0:20, [0.1, 0.5, 0.9])
3-element Vector{Float64}:
  2.0
 10.0
 18.000000000000004

julia> quantile(skipmissing([1, 10, missing]), 0.5)
5.5
```
