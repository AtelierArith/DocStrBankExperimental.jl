```
inv(x)
```

返回 `x` 的乘法逆元，使得 `x*inv(x)` 或 `inv(x)*x` 产生 [`one(x)`](@ref)（乘法单位元），并且在舍入误差范围内成立。

如果 `x` 是一个数字，这本质上与 `one(x)/x` 相同，但对于某些类型，`inv(x)` 可能会稍微高效一些。

# 示例

```jldoctest
julia> inv(2)
0.5

julia> inv(1 + 2im)
0.2 - 0.4im

julia> inv(1 + 2im) * (1 + 2im)
1.0 + 0.0im

julia> inv(2//3)
3//2
```

!!! compat "Julia 1.2"
    `inv(::Missing)` 至少需要 Julia 1.2。

