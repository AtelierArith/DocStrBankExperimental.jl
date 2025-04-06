```
cbrt(x::Real)
```

返回 `x` 的立方根，即 $x^{1/3}$。接受负值（当 $x < 0$ 时返回负实根）。

前缀运算符 `∛` 等价于 `cbrt`。

# 示例

```jldoctest
julia> cbrt(big(27))
3.0

julia> cbrt(big(-27))
-3.0
```
