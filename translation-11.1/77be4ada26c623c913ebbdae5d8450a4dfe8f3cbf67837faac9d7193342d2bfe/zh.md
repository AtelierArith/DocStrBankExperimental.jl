```
exp(x)
```

计算 `x` 的自然底数指数，换句话说就是 $ℯ^x$。

另请参见 [`exp2`](@ref)，[`exp10`](@ref) 和 [`cis`](@ref)。

# 示例

```jldoctest
julia> exp(1.0)
2.718281828459045

julia> exp(im * pi) ≈ cis(pi)
true
```
