```
round([T,] x, [r::RoundingMode])
round(x, [r::RoundingMode]; digits::Integer=0, base = 10)
round(x, [r::RoundingMode]; sigdigits::Integer, base = 10)
```

对数字 `x` 进行四舍五入。

如果没有关键字参数，`x` 将被四舍五入为整数值，返回类型为 `T` 的值，或者如果没有提供 `T`，则返回与 `x` 相同类型的值。如果该值无法用 `T` 表示，将抛出 [`InexactError`](@ref)，类似于 [`convert`](@ref)。

如果提供了 `digits` 关键字参数，则会四舍五入到小数点后指定的位数（如果为负，则在小数点前），以 `base` 为基数。

如果提供了 `sigdigits` 关键字参数，则会四舍五入到指定的有效数字，以 `base` 为基数。

[`RoundingMode`](@ref) `r` 控制四舍五入的方向；默认值为 [`RoundNearest`](@ref)，它四舍五入到最近的整数，平局（0.5 的分数值）将四舍五入到最近的偶数。请注意，如果全局四舍五入模式被更改，`round` 可能会给出不正确的结果（参见 [`rounding`](@ref)）。

在四舍五入到浮点类型时，将四舍五入到该类型可表示的整数（和 Inf），而不是实际的整数。Inf 被视为比 `floatmax(T)` 大一个 ulp，以确定“最近”，类似于 [`convert`](@ref)。

# 示例

```jldoctest
julia> round(1.7)
2.0

julia> round(Int, 1.7)
2

julia> round(1.5)
2.0

julia> round(2.5)
2.0

julia> round(pi; digits=2)
3.14

julia> round(pi; digits=3, base=2)
3.125

julia> round(123.456; sigdigits=2)
120.0

julia> round(357.913; sigdigits=4, base=2)
352.0

julia> round(Float16, typemax(UInt128))
Inf16

julia> floor(Float16, typemax(UInt128))
Float16(6.55e4)
```

!!! note
    在对二进制浮点数进行操作时，四舍五入到非 2 的指定位数可能不精确。例如，`1.15` 表示的 [`Float64`](@ref) 值实际上 *小于* 1.15，但将被四舍五入为 1.2。例如：

    ```jldoctest
    julia> x = 1.15
    1.15

    julia> big(1.15)
    1.149999999999999911182158029987476766109466552734375

    julia> x < 115//100
    true

    julia> round(x, digits=1)
    1.2
    ```


# 扩展

要将 `round` 扩展到新的数值类型，通常只需定义 `Base.round(x::NewType, r::RoundingMode)`。
