```
nextprod(factors::Union{Tuple,AbstractVector}, n)
```

大于或等于 `n` 的下一个整数，可以表示为 $\prod k_i^{p_i}$，其中 $p_1$、$p_2$ 等为整数，$k_i$ 为 `factors` 中的因子。

# 示例

```jldoctest
julia> nextprod((2, 3), 105)
108

julia> 2^2 * 3^3
108
```

!!! compat "Julia 1.6"
    接受元组的方法需要 Julia 1.6 或更高版本。

