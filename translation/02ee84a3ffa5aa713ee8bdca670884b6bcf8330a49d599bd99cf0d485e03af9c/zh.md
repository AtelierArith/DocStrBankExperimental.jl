```
log10(x)
```

计算 `x` 的以 10 为底的对数。对于负的 [`Real`](@ref) 参数会抛出 [`DomainError`](@ref)。

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log10(100)
2.0

julia> log10(2)
0.3010299956639812

julia> log10(-2)
ERROR: DomainError with -2.0:
log10 被负实数参数调用，但仅在调用复数参数时才会返回复数结果。尝试 log10(Complex(x))。
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]
```
