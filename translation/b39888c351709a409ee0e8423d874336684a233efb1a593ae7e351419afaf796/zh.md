```
rem(x, y, r::RoundingMode=RoundToZero)
```

计算 `x` 在整数除以 `y` 后的余数，商根据舍入模式 `r` 进行舍入。换句话说，数量为

```
x - y * round(x / y, r)
```

没有任何中间舍入。

  * 如果 `r == RoundNearest`，则结果是精确的，并且在区间 $[-|y| / 2, |y| / 2]$ 内。另见 [`RoundNearest`](@ref)。
  * 如果 `r == RoundToZero`（默认），则结果是精确的，并且在区间 $[0, |y|)$ 内，如果 `x` 为正，或者 $(-|y|, 0]$ 否则。另见 [`RoundToZero`](@ref)。
  * 如果 `r == RoundDown`，则结果在区间 $[0, y)$ 内，如果 `y` 为正，或者 $(y, 0]$ 否则。如果 `x` 和 `y` 符号不同，并且 `abs(x) < abs(y)`，则结果可能不精确。另见 [`RoundDown`](@ref)。
  * 如果 `r == RoundUp`，则结果在区间 $(-y, 0]$ 内，如果 `y` 为正，或者 $[0, -y)$ 否则。如果 `x` 和 `y` 符号相同，并且 `abs(x) < abs(y)`，则结果可能不精确。另见 [`RoundUp`](@ref)。
  * 如果 `r == RoundFromZero`，则结果在区间 $(-y, 0]$ 内，如果 `y` 为正，或者 $[0, -y)$ 否则。如果 `x` 和 `y` 符号相同，并且 `abs(x) < abs(y)`，则结果可能不精确。另见 [`RoundFromZero`](@ref)。

!!! compat "Julia 1.9"
    `RoundFromZero` 至少需要 Julia 1.9。


# 示例：

```jldoctest
julia> x = 9; y = 4;

julia> x % y  # 同于 rem(x, y)
1

julia> x ÷ y  # 同于 div(x, y)
2

julia> x == div(x, y) * y + rem(x, y)
true
```
