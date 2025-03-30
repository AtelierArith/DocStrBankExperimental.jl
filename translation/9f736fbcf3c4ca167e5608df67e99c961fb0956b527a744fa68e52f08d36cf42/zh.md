```
logrange(start, stop, length)
logrange(start, stop; length)
```

构造一个专门的数组，其元素在给定的端点之间以对数方式间隔。也就是说，连续元素的比率是一个常数，依据长度计算得出。

这类似于 Python 中的 `geomspace`。与 Mathematica 中的 `PowerRange` 不同，您指定的是元素的数量而不是比率。与 Python 和 Matlab 中的 `logspace` 不同，`start` 和 `stop` 参数始终是结果的第一个和最后一个元素，而不是应用于某个基数的幂。

# 示例

```jldoctest
julia> logrange(10, 4000, length=3)
3-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 10.0, 200.0, 4000.0

julia> ans[2] ≈ sqrt(10 * 4000)  # 中间元素是几何平均数
true

julia> range(10, 40, length=3)[2] ≈ (10 + 40)/2  # 算术平均数
true

julia> logrange(1f0, 32f0, 11)
11-element Base.LogRange{Float32, Float64}:
 1.0, 1.41421, 2.0, 2.82843, 4.0, 5.65685, 8.0, 11.3137, 16.0, 22.6274, 32.0

julia> logrange(1, 1000, length=4) ≈ 10 .^ (0:3)
true
```

有关更多详细信息，请参见 [`LogRange`](@ref Base.LogRange) 类型。

另请参见 [`range`](@ref) 以获取线性间隔的点。

!!! compat "Julia 1.11"
    此函数至少需要 Julia 1.11。

