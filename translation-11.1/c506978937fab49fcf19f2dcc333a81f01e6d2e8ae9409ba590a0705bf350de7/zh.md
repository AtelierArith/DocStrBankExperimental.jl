```
argmin(f, domain)
```

返回一个来自 `domain` 的值 `x`，使得 `f(x)` 最小。如果 `f(x)` 有多个最小值，则将找到第一个。

`domain` 必须是一个非空的可迭代对象。

`NaN` 被视为小于所有其他值，除了 `missing`。

!!! compat "Julia 1.7"
    此方法需要 Julia 1.7 或更高版本。


另见 [`argmax`](@ref), [`findmin`](@ref).

# 示例

```jldoctest
julia> argmin(sign, -10:5)
-10

julia> argmin(x -> -x^3 + x^2 - 10, -5:5)
5

julia> argmin(acos, 0:0.1:1)
1.0
```
