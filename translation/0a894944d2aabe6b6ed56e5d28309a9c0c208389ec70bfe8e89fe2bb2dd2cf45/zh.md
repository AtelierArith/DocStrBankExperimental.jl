```
I
```

一个类型为 [`UniformScaling`](@ref) 的对象，表示任意大小的单位矩阵。

# 示例

```jldoctest
julia> fill(1, (5,6)) * I == fill(1, (5,6))
true

julia> [1 2im 3; 1im 2 3] * I
2×3 矩阵{复数{Int64}}:
 1+0im  0+2im  3+0im
 0+1im  2+0im  3+0im
```
