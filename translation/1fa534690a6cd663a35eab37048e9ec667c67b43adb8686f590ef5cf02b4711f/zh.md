```
log2(x)
```

计算 `x` 的以 2 为底的对数。对于负的 [`Real`](@ref) 参数会抛出 [`DomainError`](@ref)。

另请参见：[`exp2`](@ref)，[`ldexp`](@ref)，[`ispow2`](@ref)。

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log2(4)
2.0

julia> log2(10)
3.321928094887362

julia> log2(-2)
ERROR: DomainError with -2.0:
log2 被负实数参数调用，但仅在使用复数参数时才会返回复数结果。尝试 log2(Complex(x))。
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]

julia> log2.(2.0 .^ (-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```
