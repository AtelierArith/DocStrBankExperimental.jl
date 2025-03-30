```
clamp!(array::AbstractArray, lo, hi)
```

将 `array` 中的值限制在指定范围内，原地修改。另见 [`clamp`](@ref)。

!!! compat "Julia 1.3"
    `array` 中的 `missing` 条目至少需要 Julia 1.3。


# 示例

```jldoctest
julia> row = collect(-4:4)';

julia> clamp!(row, 0, Inf)
1×9 adjoint(::Vector{Int64}) with eltype Int64:
 0  0  0  0  0  1  2  3  4

julia> clamp.((-4:4)', 0, Inf)
1×9 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  1.0  2.0  3.0  4.0
```
