```
significand(x)
```

提取浮点数的有效数字（也称为尾数）。如果 `x` 是一个非零有限数，则结果将是与 `x` 相同类型和符号的数字，其绝对值在区间 $[1,2)$ 上。否则返回 `x`。

另请参见 [`frexp`](@ref), [`exponent`](@ref)。

# 示例

```jldoctest
julia> significand(15.2)
1.9

julia> significand(-15.2)
-1.9

julia> significand(-15.2) * 2^3
-15.2

julia> significand(-Inf), significand(Inf), significand(NaN)
(-Inf, Inf, NaN)
```
