```
randexp([rng=default_rng()], [T=Float64], [dims...])
```

根据指数分布生成类型为 `T` 的随机数，规模为 1。可选地生成这样的随机数数组。`Base` 模块目前为类型 [`Float16`](@ref)、[`Float32`](@ref) 和 [`Float64`](@ref)（默认）提供了实现。

# 示例

```jldoctest
julia> rng = Xoshiro(123);

julia> randexp(rng, Float32)
1.1757717f0

julia> randexp(rng, 3, 3)
3×3 Matrix{Float64}:
 1.37766  0.456653  0.236418
 3.40007  0.229917  0.0684921
 0.48096  0.577481  0.71835
```
