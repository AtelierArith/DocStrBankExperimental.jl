```
unsafe_trunc(T, x)
```

返回类型 `T` 的最近整数值，其绝对值小于或等于 `x` 的绝对值。如果该值无法被 `T` 表示，将返回一个任意值。另见 [`trunc`](@ref)。

# 示例

```jldoctest
julia> unsafe_trunc(Int, -2.2)
-2

julia> unsafe_trunc(Int, NaN)
-9223372036854775808
```
