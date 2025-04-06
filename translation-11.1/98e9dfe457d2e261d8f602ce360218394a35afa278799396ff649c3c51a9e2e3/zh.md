```
printstyled([io], xs...; bold::Bool=false, italic::Bool=false, underline::Bool=false, blink::Bool=false, reverse::Bool=false, hidden::Bool=false, color::Union{Symbol,Int}=:normal)
```

以符号或整数指定的颜色打印 `xs`，可选地以粗体显示。

关键字 `color` 可以取以下任意值 `:normal`, `:italic`, `:default`, `:bold`, `:black`, `:blink`, `:blue`, `:cyan`, `:green`, `:hidden`, `:light_black`, `:light_blue`, `:light_cyan`, `:light_green`, `:light_magenta`, `:light_red`, `:light_white`, `:light_yellow`, `:magenta`, `:nothing`, `:red`, `:reverse`, `:underline`, `:white`, 或 `:yellow`，或一个介于 0 和 255 之间的整数（包括 0 和 255）。请注意，并非所有终端都支持 256 种颜色。

关键字 `bold=true`、`italic=true`、`underline=true`、`blink=true` 是不言自明的。关键字 `reverse=true` 以交换前景和背景颜色的方式打印，而 `hidden=true` 在终端中应不可见，但仍可被复制。这些属性可以以任意组合使用。

另见 [`print`](@ref), [`println`](@ref), [`show`](@ref).

!!! note
    并非所有终端都支持斜体输出。一些终端将斜体解释为反转或闪烁。


!!! compat "Julia 1.7"
    除 `color` 和 `bold` 外的关键字是在 Julia 1.7 中添加的。


!!! compat "Julia 1.10"
    在 Julia 1.10 中添加了对斜体输出的支持。

