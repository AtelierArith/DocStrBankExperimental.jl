```
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]])
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; digits=0, base=10)
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; sigdigits, base=10)
```

返回与复数值 `z` 最近的整数值，类型与 `z` 相同，使用指定的 [`RoundingMode`](@ref) 进行平局处理。第一个 [`RoundingMode`](@ref) 用于舍入实部，而第二个用于舍入虚部。

`RoundingModeReal` 和 `RoundingModeImaginary` 默认为 [`RoundNearest`](@ref)，它舍入到最近的整数，平局（0.5 的分数值）舍入到最近的偶数整数。

# 示例

```jldoctest
julia> round(3.14 + 4.5im)
3.0 + 4.0im

julia> round(3.14 + 4.5im, RoundUp, RoundNearestTiesUp)
4.0 + 5.0im

julia> round(3.14159 + 4.512im; digits = 1)
3.1 + 4.5im

julia> round(3.14159 + 4.512im; sigdigits = 3)
3.14 + 4.51im
```
