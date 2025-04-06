```
nextprod(factors::Union{Tuple,AbstractVector}, n)
```

`n`以上の次の整数で、`factors`の要素である整数 $k_i$ に対して $\prod k_i^{p_i}$ の形で表すことができるもの。

# 例

```jldoctest
julia> nextprod((2, 3), 105)
108

julia> 2^2 * 3^3
108
```

!!! compat "Julia 1.6"
    タプルを受け入れるメソッドは、Julia 1.6以降が必要です。

