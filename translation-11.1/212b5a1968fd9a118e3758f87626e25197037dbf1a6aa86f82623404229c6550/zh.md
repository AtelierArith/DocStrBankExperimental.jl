```
frexp(val)
```

返回 `(x,exp)`，使得 `x` 的大小在区间 $[1/2, 1)$ 或 0，并且 `val` 等于 $x \times 2^{exp}$。

另见 [`significand`](@ref), [`exponent`](@ref), [`ldexp`](@ref)。

# 示例

```jldoctest
julia> frexp(6.0)
(0.75, 3)

julia> significand(6.0), exponent(6.0)  # 区间 [1, 2) 代替
(1.5, 2)

julia> frexp(0.0), frexp(NaN), frexp(-Inf)  # 指数会导致错误
((0.0, 0), (NaN, 0), (-Inf, 0))
```
