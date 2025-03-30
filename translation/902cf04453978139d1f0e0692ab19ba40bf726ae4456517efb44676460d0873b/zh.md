```
exp2(x)
```

计算 `x` 的以 2 为底的指数，换句话说就是 $2^x$。

另见 [`ldexp`](@ref), [`<<`](@ref)。

# 示例

```jldoctest
julia> exp2(5)
32.0

julia> 2^5
32

julia> exp2(63) > typemax(Int)
true
```
