```
eps(x::AbstractFloat)
```

返回 `x` 的 *最后一位单位* (ulp)。这是在 `x` 处连续可表示浮点值之间的距离。在大多数情况下，如果 `x` 两侧的距离不同，则取两者中较大的一个，即

```
eps(x) == max(x-prevfloat(x), nextfloat(x)-x)
```

这个规则的例外是最小和最大有限值（例如 [`Float64`](@ref) 的 `nextfloat(-Inf)` 和 `prevfloat(Inf)`），它们会舍入到较小的值。

这种行为的理由是 `eps` 界定了浮点舍入误差。在默认的 `RoundNearest` 舍入模式下，如果 $y$ 是一个实数，而 $x$ 是离 $y$ 最近的浮点数，则

$$
|y-x| \leq \operatorname{eps}(x)/2.
$$

另请参见: [`nextfloat`](@ref), [`issubnormal`](@ref), [`floatmax`](@ref).

# 示例

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(prevfloat(2.0))
2.220446049250313e-16

julia> eps(2.0)
4.440892098500626e-16

julia> x = prevfloat(Inf)      # 最大有限 Float64
1.7976931348623157e308

julia> x + eps(x)/2            # 向上舍入
Inf

julia> x + prevfloat(eps(x)/2) # 向下舍入
1.7976931348623157e308
```
