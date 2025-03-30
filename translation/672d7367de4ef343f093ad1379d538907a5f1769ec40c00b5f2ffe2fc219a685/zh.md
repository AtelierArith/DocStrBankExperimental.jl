```
@printf([io::IO], "%Fmt", args...)
```

使用 C `printf` 风格的格式说明字符串打印 `args`。可选地，可以将 `IO` 作为第一个参数传递以重定向输出。

# 示例

```jldoctest
julia> @printf "Hello %s" "world"
Hello world

julia> @printf "Scientific notation %e" 1.234
Scientific notation 1.234000e+00

julia> @printf "Scientific notation three digits %.3e" 1.23456
Scientific notation three digits 1.235e+00

julia> @printf "Decimal two digits %.2f" 1.23456
Decimal two digits 1.23

julia> @printf "Padded to length 5 %5i" 123
Padded to length 5   123

julia> @printf "Padded with zeros to length 6 %06i" 123
Padded with zeros to length 6 000123

julia> @printf "Use shorter of decimal or scientific %g %g" 1.23 12300000.0
Use shorter of decimal or scientific 1.23 1.23e+07

julia> @printf "Use dynamic width and precision  %*.*f" 10 2 0.12345
Use dynamic width and precision        0.12
```

有关格式的系统说明，请参见 [here](https://en.cppreference.com/w/c/io/fprintf)。另请参见 [`@sprintf`](@ref) 以获取结果作为 `String` 而不是打印出来。

# 注意事项

`Inf` 和 `NaN` 在标志 `%a`、`%A`、`%e`、`%E`、`%f`、`%F`、`%g` 和 `%G` 中始终打印为 `Inf` 和 `NaN`。此外，如果一个浮点数与两个可能的输出字符串的数值相等，则选择离零更远的输出字符串。

# 示例

```jldoctest
julia> @printf("%f %F %f %F", Inf, Inf, NaN, NaN)
Inf Inf NaN NaN

julia> @printf "%.0f %.1f %f" 0.5 0.025 -0.0078125
0 0.0 -0.007812
```

!!! compat "Julia 1.8"
    从 Julia 1.8 开始，`%s`（字符串）和 `%c`（字符）的宽度是使用 [`textwidth`](@ref) 计算的，例如，它忽略零宽字符（如组合字符用于变音符号）并将某些“宽”字符（如表情符号）视为宽度 `2`。


!!! compat "Julia 1.10"
    动态宽度说明符如 `%*s` 和 `%0*.*f` 需要 Julia 1.10。

