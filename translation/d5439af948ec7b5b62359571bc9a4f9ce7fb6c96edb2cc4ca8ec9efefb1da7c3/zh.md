```
CartesianIndices(sz::Dims) -> R
CartesianIndices((istart:[istep:]istop, jstart:[jstep:]jstop, ...)) -> R
```

定义一个区域 `R`，跨越一个多维矩形范围的整数索引。这些索引最常见于迭代的上下文中，其中 `for I in R ... end` 将返回与嵌套循环等效的 [`CartesianIndex`](@ref) 索引 `I`

```
for j = jstart:jstep:jstop
    for i = istart:istep:istop
        ...
    end
end
```

因此，这些对于编写在任意维度中工作的算法非常有用。

```
CartesianIndices(A::AbstractArray) -> R
```

作为一种便利，从数组构造 `CartesianIndices` 会生成其索引的范围。

!!! compat "Julia 1.6"
    步长范围方法 `CartesianIndices((istart:istep:istop, jstart:[jstep:]jstop, ...))` 至少需要 Julia 1.6。


# 示例

```jldoctest
julia> foreach(println, CartesianIndices((2, 2, 2)))
CartesianIndex(1, 1, 1)
CartesianIndex(2, 1, 1)
CartesianIndex(1, 2, 1)
CartesianIndex(2, 2, 1)
CartesianIndex(1, 1, 2)
CartesianIndex(2, 1, 2)
CartesianIndex(1, 2, 2)
CartesianIndex(2, 2, 2)

julia> CartesianIndices(fill(1, (2,3)))
CartesianIndices((2, 3))
```

## 线性索引与笛卡尔索引之间的转换

线性索引到笛卡尔索引的转换利用了 `CartesianIndices` 是一个 `AbstractArray` 并且可以线性索引的事实：

```jldoctest
julia> cartesian = CartesianIndices((1:3, 1:2))
CartesianIndices((1:3, 1:2))

julia> cartesian[4]
CartesianIndex(1, 2)

julia> cartesian = CartesianIndices((1:2:5, 1:2))
CartesianIndices((1:2:5, 1:2))

julia> cartesian[2, 2]
CartesianIndex(3, 2)
```

## 广播

`CartesianIndices` 支持与 `CartesianIndex` 的广播算术 (+ 和 -)。

!!! compat "Julia 1.1"
    `CartesianIndices` 的广播至少需要 Julia 1.1。


```jldoctest
julia> CIs = CartesianIndices((2:3, 5:6))
CartesianIndices((2:3, 5:6))

julia> CI = CartesianIndex(3, 4)
CartesianIndex(3, 4)

julia> CIs .+ CI
CartesianIndices((5:6, 9:10))
```

有关笛卡尔到线性索引转换，请参见 [`LinearIndices`](@ref)。
