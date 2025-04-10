```
mod2pi(x)
```

在除以 `2π` 后的模，返回范围 $[0,2π)$。

此函数计算除以数值精确的 `2π` 后的模的浮点表示，因此与 `mod(x,2π)` 并不完全相同，后者计算的是相对于浮点数 `2π` 的 `x` 的模。

!!! note
    根据输入值的格式，最接近的可表示值可能小于 2π。例如，表达式 `mod2pi(2π)` 不会返回 `0`，因为中间值 `2*π` 是 `Float64` 类型，而 `2*Float64(π) < 2*big(π)`。有关此行为的更精细控制，请参见 [`rem2pi`](@ref)。


# 示例

```jldoctest
julia> mod2pi(9*pi/4)
0.7853981633974481
```
