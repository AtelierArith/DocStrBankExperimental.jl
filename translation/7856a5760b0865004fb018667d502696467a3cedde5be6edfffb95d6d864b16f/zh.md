```
RoundingMode
```

用于控制浮点运算的舍入模式的类型（通过 [`rounding`](@ref)/[`setrounding`](@ref) 函数），或作为舍入到最接近整数的可选参数（通过 [`round`](@ref) 函数）。

当前支持的舍入模式有：

  * [`RoundNearest`](@ref)（默认）
  * [`RoundNearestTiesAway`](@ref)
  * [`RoundNearestTiesUp`](@ref)
  * [`RoundToZero`](@ref)
  * [`RoundFromZero`](@ref)
  * [`RoundUp`](@ref)
  * [`RoundDown`](@ref)

!!! compat "Julia 1.9"
    `RoundFromZero` 至少需要 Julia 1.9。之前的版本仅支持 `BigFloat` 的 `RoundFromZero`。

