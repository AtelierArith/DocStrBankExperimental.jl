```
eps(::Type{T}) where T<:AbstractFloat
eps()
```

返回浮点类型 `T` 的 *机器精度*（默认 `T = Float64`）。这被定义为 1 和 `typeof(one(T))` 可表示的下一个最大值之间的间隔，并且等同于 `eps(one(T))`。 （由于 `eps(T)` 是 `T` 的 *相对误差* 的界限，它是一个“无量纲”的量，如 [`one`](@ref) 所示。）

# 示例

```jldoctest
julia> eps()
2.220446049250313e-16

julia> eps(Float32)
1.1920929f-7

julia> 1.0 + eps()
1.0000000000000002

julia> 1.0 + eps()/2
1.0
```
