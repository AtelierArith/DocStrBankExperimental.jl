```
LogRange{T}(start, stop, len) <: AbstractVector{T}
```

一个范围，其元素在 `start` 和 `stop` 之间以对数方式间隔，间隔由 `len` 控制。由 [`logrange`](@ref) 返回。

与 [`LinRange`](@ref) 类似，第一个和最后一个元素将正好是提供的值，但中间值可能会有小的浮点误差。这些值是使用端点的对数计算的，这些对数在构造时存储，通常比 `T` 具有更高的精度。

# 示例

```jldoctest
julia> logrange(1, 4, length=5)
5-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 1.0, 1.41421, 2.0, 2.82843, 4.0

julia> Base.LogRange{Float16}(1, 4, 5)
5-element Base.LogRange{Float16, Float64}:
 1.0, 1.414, 2.0, 2.828, 4.0

julia> logrange(1e-310, 1e-300, 11)[1:2:end]
6-element Vector{Float64}:
 1.0e-310
 9.999999999999974e-309
 9.999999999999981e-307
 9.999999999999988e-305
 9.999999999999994e-303
 1.0e-300

julia> prevfloat(1e-308, 5) == ans[2]
true
```

请注意，不允许整数类型 `T`。例如，可以使用 `round.(Int, xs)`，或某个整数基数的显式幂：

```jldoctest
julia> xs = logrange(1, 512, 4)
4-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 1.0, 8.0, 64.0, 512.0

julia> 2 .^ (0:3:9) |> println
[1, 8, 64, 512]
```

!!! compat "Julia 1.11"
    此类型至少需要 Julia 1.11。

