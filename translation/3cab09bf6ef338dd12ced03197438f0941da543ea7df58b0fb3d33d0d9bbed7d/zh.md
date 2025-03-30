```
rank(A::AbstractMatrix; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
rank(A::AbstractMatrix, rtol::Real)
```

通过计算 `svdvals(A)` 的输出中有多少个大于 `max(atol, rtol*σ₁)` 来计算矩阵的数值秩，其中 `σ₁` 是 `A` 的最大计算奇异值。`atol` 和 `rtol` 分别是绝对和相对容差。默认的相对容差是 `n*ϵ`，其中 `n` 是 `A` 最小维度的大小，`ϵ` 是 `A` 元素类型的 [`eps`](@ref)。

!!! note
    数值秩可能是对病态矩阵的敏感和不精确的表征，这些矩阵的奇异值接近阈值容差 `max(atol, rtol*σ₁)`。在这种情况下，对奇异值计算或矩阵的轻微扰动可能会通过推动一个或多个奇异值跨越阈值而改变 `rank` 的结果。这些变化甚至可能由于不同 Julia 版本、架构、编译器或操作系统之间的浮点错误变化而发生。


!!! compat "Julia 1.1"
    `atol` 和 `rtol` 关键字参数需要至少 Julia 1.1。在 Julia 1.0 中，`rtol` 作为位置参数可用，但在 Julia 2.0 中将被弃用。


# 示例

```jldoctest
julia> rank(Matrix(I, 3, 3))
3

julia> rank(diagm(0 => [1, 0, 2]))
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.1)
2

julia> rank(diagm(0 => [1, 0.001, 2]), rtol=0.00001)
3

julia> rank(diagm(0 => [1, 0.001, 2]), atol=1.5)
1
```
