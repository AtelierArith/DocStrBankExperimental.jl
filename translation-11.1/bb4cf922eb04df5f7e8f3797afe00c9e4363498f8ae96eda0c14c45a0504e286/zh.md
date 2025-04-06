```
Inf, Inf64
```

类型为 [`Float64`](@ref) 的正无穷。

另请参见：[`isfinite`](@ref), [`typemax`](@ref), [`NaN`](@ref), [`Inf32`](@ref)。

# 示例

```jldoctest
julia> π/0
Inf

julia> +1.0 / -0.0
-Inf

julia> ℯ^-Inf
0.0
```
