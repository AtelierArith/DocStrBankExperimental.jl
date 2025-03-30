```
sqrt(x)
```

返回 $\sqrt{x}$。

对于负的 [`Real`](@ref) 参数会抛出 [`DomainError`](@ref)。请改用复数负参数。请注意，`sqrt` 在负实轴上有一个分支切割。

前缀运算符 `√` 等同于 `sqrt`。

另请参见: [`hypot`](@ref)。

# 示例

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> sqrt(big(81))
9.0

julia> sqrt(big(-81))
ERROR: DomainError with -81.0:
NaN result for non-NaN input.
Stacktrace:
 [1] sqrt(::BigFloat) at ./mpfr.jl:501
[...]

julia> sqrt(big(complex(-81)))
0.0 + 9.0im

julia> sqrt(-81 - 0.0im)  # -0.0im 在分支切割下方
0.0 - 9.0im

julia> .√(1:4)
4-element Vector{Float64}:
 1.0
 1.4142135623730951
 1.7320508075688772
 2.0
```
