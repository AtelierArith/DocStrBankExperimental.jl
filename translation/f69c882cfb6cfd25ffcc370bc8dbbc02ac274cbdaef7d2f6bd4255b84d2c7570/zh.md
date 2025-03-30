```
isodd(x::Number) -> Bool
```

如果 `x` 是一个奇数整数（即，不可被 2 整除的整数），则返回 `true`，否则返回 `false`。

!!! compat "Julia 1.7"
    非 `Integer` 参数需要 Julia 1.7 或更高版本。


# 示例

```jldoctest
julia> isodd(9)
true

julia> isodd(10)
false
```
