```
log1p(x)
```

准确的自然对数 `1+x`。对于小于 -1 的 [`Real`](@ref) 参数会抛出 [`DomainError`](@ref)。

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log1p(-0.5)
-0.6931471805599453

julia> log1p(0)
0.0

julia> log1p(-2)
错误：-2.0 的 DomainError：
log1p 被调用时实数参数 < -1，但仅在使用复数参数时才会返回复数结果。尝试 log1p(Complex(x))。
堆栈跟踪：
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```
