```
exponent(x::Real) -> Int
```

返回最大的整数 `y`，使得 `2^y ≤ abs(x)`。

当 `x` 为零、无穷大或 [`NaN`](@ref) 时抛出 `DomainError`。对于任何其他非次正常浮点数 `x`，这对应于 `x` 的指数位。

另请参见 [`signbit`](@ref), [`significand`](@ref), [`frexp`](@ref), [`issubnormal`](@ref), [`log2`](@ref), [`ldexp`](@ref)。

# 示例

```jldoctest
julia> exponent(8)
3

julia> exponent(6.5)
2

julia> exponent(-1//4)
-2

julia> exponent(3.142e-4)
-12

julia> exponent(floatmin(Float32)), exponent(nextfloat(0.0f0))
(-126, -149)

julia> exponent(0.0)
ERROR: DomainError with 0.0:
Cannot be ±0.0.
[...]
```
