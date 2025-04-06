```
argmax(f, domain)
```

从 `domain` 返回一个值 `x`，使得 `f(x)` 达到最大值。如果 `f(x)` 有多个最大值，则将找到第一个。

`domain` 必须是一个非空的可迭代对象。

值的比较使用 `isless`。

!!! compat "Julia 1.7"
    此方法需要 Julia 1.7 或更高版本。


另请参见 [`argmin`](@ref)，[`findmax`](@ref)。

# 示例

```jldoctest
julia> argmax(abs, -10:5)
-10

julia> argmax(cos, 0:π/2:2π)
0.0
```
