```
extrema(f, itr; [init]) -> (mn, mx)
```

计算应用于 `itr` 中每个元素的函数 `f` 的最小值 `mn` 和最大值 `mx`，并将它们作为一个 2 元组返回。只对 `itr` 进行一次遍历。

对于空的 `itr`，返回的值可以通过 `init` 指定。它必须是一个 2 元组，其第一个和第二个元素分别是 `min` 和 `max` 的中性元素（即大于/小于或等于任何其他元素）。它用于非空集合。注意：这意味着，对于空的 `itr`，返回的值 `(mn, mx)` 满足 `mn ≥ mx`，尽管对于非空的 `itr`，它满足 `mn ≤ mx`。这是一个“悖论”，但却是预期的结果。

!!! compat "Julia 1.2"
    此方法需要 Julia 1.2 或更高版本。


!!! compat "Julia 1.8"
    关键字参数 `init` 需要 Julia 1.8 或更高版本。


# 示例

```jldoctest
julia> extrema(sin, 0:π)
(0.0, 0.9092974268256817)

julia> extrema(sin, Real[]; init = (1.0, -1.0))  # 好，因为 -1 ≤ sin(::Real) ≤ 1
(1.0, -1.0)
```
