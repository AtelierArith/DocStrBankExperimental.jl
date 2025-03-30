```
abs(x)
```

`x` 的绝对值。

当 `abs` 应用于有符号整数时，可能会发生溢出，导致返回负值。此溢出仅在 `abs` 应用于有符号整数的最小可表示值时发生。也就是说，当 `x == typemin(typeof(x))` 时，`abs(x) == x < 0`，而不是 `-x`，这可能是预期的结果。

另请参见: [`abs2`](@ref), [`unsigned`](@ref), [`sign`](@ref)。

# 示例

```jldoctest
julia> abs(-3)
3

julia> abs(1 + im)
1.4142135623730951

julia> abs.(Int8[-128 -127 -126 0 126 127])  # 在 typemin(Int8) 处溢出
1×6 Matrix{Int8}:
 -128  127  126  0  126  127

julia> maximum(abs, [1, -2, 3, -4])
4
```
