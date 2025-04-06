```
isreal(x) -> Bool
```

测试 `x` 或其所有元素是否在数值上等于某个实数，包括无穷大和 NaN。如果 `isequal(x, real(x))` 为真，则 `isreal(x)` 为真。

# 示例

```jldoctest
julia> isreal(5.)
true

julia> isreal(1 - 3im)
false

julia> isreal(Inf + 0im)
true

julia> isreal([4.; complex(0,1)])
false
```
