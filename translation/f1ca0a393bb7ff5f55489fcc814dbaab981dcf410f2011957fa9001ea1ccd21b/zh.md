```
extrema(itr; [init]) -> (mn, mx)
```

计算单次遍历中的最小值 `mn` 和最大值 `mx`，并将它们作为一个 2 元组返回。

对于空的 `itr`，返回的值可以通过 `init` 指定。它必须是一个 2 元组，其第一个和第二个元素分别是 `min` 和 `max` 的中性元素（即大于/小于或等于任何其他元素）。因此，当 `itr` 为空时，返回的 `(mn, mx)` 元组将满足 `mn ≥ mx`。当指定 `init` 时，即使对于非空的 `itr` 也可以使用它。

!!! compat "Julia 1.8"
    关键字参数 `init` 需要 Julia 1.8 或更高版本。


# 示例

```jldoctest
julia> extrema(2:10)
(2, 10)

julia> extrema([9,pi,4.5])
(3.141592653589793, 9.0)

julia> extrema([]; init = (Inf, -Inf))
(Inf, -Inf)
```
