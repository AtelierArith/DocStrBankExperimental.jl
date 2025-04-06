```
parse(type, str; base)
```

将字符串解析为数字。对于 `Integer` 类型，可以指定基数（默认是 10）。对于浮点类型，字符串被解析为十进制浮点数。 `Complex` 类型从形式为 `"R±Iim"` 的十进制字符串解析为请求类型的 `Complex(R,I)`；可以使用 `"i"` 或 `"j"` 替代 `"im"`，并且 `"R"` 或 `"Iim"` 也是允许的。如果字符串不包含有效数字，则会引发错误。

!!! compat "Julia 1.1"
    `parse(Bool, str)` 至少需要 Julia 1.1。


# 示例

```jldoctest
julia> parse(Int, "1234")
1234

julia> parse(Int, "1234", base = 5)
194

julia> parse(Int, "afc", base = 16)
2812

julia> parse(Float64, "1.2e-3")
0.0012

julia> parse(Complex{Float64}, "3.2e-1 + 4.5im")
0.32 + 4.5im
```
