```
log(b,x)
```

计算 `x` 的底为 `b` 的对数。对于负的 [`Real`](@ref) 参数会抛出 [`DomainError`](@ref)。

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(4,8)
1.5

julia> log(4,2)
0.5

julia> log(-2, 3)
ERROR: DomainError with -2.0:
log 被调用时使用了负的实数参数，但仅在使用复数参数时才会返回复数结果。尝试 log(Complex(x))。
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(2, -3)
ERROR: DomainError with -3.0:
log 被调用时使用了负的实数参数，但仅在使用复数参数时才会返回复数结果。尝试 log(Complex(x))。
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```

!!! note
    如果 `b` 是 2 或 10 的幂，应该使用 [`log2`](@ref) 或 [`log10`](@ref)，因为这些通常会更快且更准确。例如，

    ```jldoctest
    julia> log(100,1000000)
    2.9999999999999996

    julia> log10(1000000)/2
    3.0
    ```

