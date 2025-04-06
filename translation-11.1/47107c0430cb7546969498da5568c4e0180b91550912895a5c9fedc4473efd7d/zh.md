```
log(x)
```

计算 `x` 的自然对数。

对于负的 [`Real`](@ref) 参数会抛出 [`DomainError`](@ref)。使用复数参数可以获得复数结果。沿负实轴有一个分支切割，其中 `-0.0im` 被视为在轴下方。

另请参见 [`ℯ`](@ref), [`log1p`](@ref), [`log2`](@ref), [`log10`](@ref)。

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(2)
0.6931471805599453

julia> log(-3)
ERROR: DomainError with -3.0:
log 被调用时使用了负实参数，但仅在使用复数参数时才会返回复数结果。尝试 log(Complex(x))。
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(-3 + 0im)
1.0986122886681098 + 3.141592653589793im

julia> log(-3 - 0.0im)
1.0986122886681098 - 3.141592653589793im

julia> log.(exp.(-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```
