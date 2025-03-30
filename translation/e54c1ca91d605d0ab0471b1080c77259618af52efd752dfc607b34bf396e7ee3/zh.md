```
rem2pi(x, r::RoundingMode)
```

计算 `x` 在整数除以 `2π` 后的余数，商根据舍入模式 `r` 进行舍入。换句话说，该量为

```
x - 2π*round(x/(2π),r)
```

没有任何中间舍入。这内部使用了 `2π` 的高精度近似，因此将给出比 `rem(x,2π,r)` 更准确的结果。

  * 如果 `r == RoundNearest`，则结果在区间 $[-π, π]$ 内。这通常是最准确的结果。另见 [`RoundNearest`](@ref)。
  * 如果 `r == RoundToZero`，则结果在区间 $[0, 2π]$ 内（如果 `x` 为正），或者在 $[-2π, 0]$ 内（否则）。另见 [`RoundToZero`](@ref)。
  * 如果 `r == RoundDown`，则结果在区间 $[0, 2π]$ 内。另见 [`RoundDown`](@ref)。
  * 如果 `r == RoundUp`，则结果在区间 $[-2π, 0]$ 内。另见 [`RoundUp`](@ref)。

# 示例

```jldoctest
julia> rem2pi(7pi/4, RoundNearest)
-0.7853981633974485

julia> rem2pi(7pi/4, RoundDown)
5.497787143782138
```
