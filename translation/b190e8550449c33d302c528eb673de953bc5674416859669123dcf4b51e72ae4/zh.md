```
RoundFromZero
```

从零舍入。

!!! compat "Julia 1.9"
    `RoundFromZero` 至少需要 Julia 1.9。之前的版本仅支持 `BigFloat` 的 `RoundFromZero`。


# 示例

```jldoctest
julia> BigFloat("1.0000000000000001", 5, RoundFromZero)
1.06
```
