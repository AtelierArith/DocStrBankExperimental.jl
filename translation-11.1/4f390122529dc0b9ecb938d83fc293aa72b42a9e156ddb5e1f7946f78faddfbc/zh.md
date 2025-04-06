```
div(x, y, r::RoundingMode=RoundToZero)
```

欧几里得（整数）除法的商。计算 `x / y`，根据舍入模式 `r` 四舍五入为整数。换句话说，该数量为

```
round(x / y, r)
```

而没有任何中间舍入。

!!! compat "Julia 1.4"
    三个参数的方法需要 Julia 1.4 或更高版本。


另请参见 [`fld`](@ref) 和 [`cld`](@ref)，它们是此函数的特例。

!!! compat "Julia 1.9"
    `RoundFromZero` 至少需要 Julia 1.9。


# 示例：

```jldoctest
julia> div(4, 3, RoundToZero) # 匹配 div(4, 3)
1
julia> div(4, 3, RoundDown) # 匹配 fld(4, 3)
1
julia> div(4, 3, RoundUp) # 匹配 cld(4, 3)
2
julia> div(5, 2, RoundNearest)
2
julia> div(5, 2, RoundNearestTiesAway)
3
julia> div(-5, 2, RoundNearest)
-2
julia> div(-5, 2, RoundNearestTiesAway)
-3
julia> div(-5, 2, RoundNearestTiesUp)
-2
julia> div(4, 3, RoundFromZero)
2
julia> div(-4, 3, RoundFromZero)
-2
```
