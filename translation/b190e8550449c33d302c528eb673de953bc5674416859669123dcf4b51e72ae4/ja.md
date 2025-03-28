```
RoundFromZero
```

ゼロから離れるように丸めます。

!!! compat "Julia 1.9"
    `RoundFromZero` は少なくとも Julia 1.9 が必要です。以前のバージョンは `BigFloat` のみで `RoundFromZero` をサポートしています。


# 例

```jldoctest
julia> BigFloat("1.0000000000000001", 5, RoundFromZero)
1.06
```
