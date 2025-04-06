```
abs2(x)
```

`x` 的平方绝对值。

这比 `abs(x)^2` 更快，特别是对于复杂数，因为 `abs(x)` 需要通过 [`hypot`](@ref) 计算平方根。

另见 [`abs`](@ref), [`conj`](@ref), [`real`](@ref)。

# 示例

```jldoctest
julia> abs2(-3)
9

julia> abs2(3.0 + 4.0im)
25.0

julia> sum(abs2, [1+2im, 3+4im])  # LinearAlgebra.norm(x)^2
30
```
