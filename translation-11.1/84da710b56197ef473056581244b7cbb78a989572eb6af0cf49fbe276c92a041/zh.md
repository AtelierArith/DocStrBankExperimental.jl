```
LinRange{T,L}
```

一个范围，包含 `len` 个在其 `start` 和 `stop` 之间线性间隔的元素。间隔的大小由 `len` 控制，`len` 必须是一个 `Integer`。

# 示例

```jldoctest
julia> LinRange(1.5, 5.5, 9)
9-element LinRange{Float64, Int64}:
 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5, 5.0, 5.5
```

与使用 [`range`](@ref) 相比，直接构造 `LinRange` 应该有更少的开销，但不会尝试纠正浮点错误：

```jldoctest
julia> collect(range(-0.1, 0.3, length=5))
5-element Vector{Float64}:
 -0.1
  0.0
  0.1
  0.2
  0.3

julia> collect(LinRange(-0.1, 0.3, 5))
5-element Vector{Float64}:
 -0.1
 -1.3877787807814457e-17
  0.09999999999999999
  0.19999999999999998
  0.3
```

另请参见 [`Logrange`](@ref Base.LogRange) 以获取对数间隔的点。
