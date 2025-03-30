```
iseven(x::Number) -> Bool
```

如果 `x` 是一个偶数整数（即，可以被 2 整除的整数），则返回 `true`，否则返回 `false`。

!!! compat "Julia 1.7"
    非 `Integer` 参数需要 Julia 1.7 或更高版本。


# 示例

```jldoctest
julia> iseven(9)
false

julia> iseven(10)
true
```
