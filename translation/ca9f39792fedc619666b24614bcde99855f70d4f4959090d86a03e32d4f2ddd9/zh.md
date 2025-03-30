```
divrem(x, y, r::RoundingMode=RoundToZero)
```

欧几里得除法的商和余数。等价于 `(div(x, y, r), rem(x, y, r))`。同样地，使用默认值 `r` 时，此调用等价于 `(x ÷ y, x % y)`。

另见: [`fldmod`](@ref), [`cld`](@ref)。

# 示例

```jldoctest
julia> divrem(3, 7)
(0, 3)

julia> divrem(7, 3)
(2, 1)
```
