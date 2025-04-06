```
eigvals!(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

与 [`eigvals`](@ref) 相同，但通过覆盖输入 `A` 来节省空间，而不是创建副本。`permute`、`scale` 和 `sortby` 关键字与 [`eigen`](@ref) 相同。

!!! note
    在对输入矩阵 `A` 调用 `eigvals!` 后，`A` 将不包含其特征值 - `A` 被用作工作空间。


# 示例

```jldoctest
julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> eigvals!(A)
2-element Vector{Float64}:
 -0.3722813232690143
  5.372281323269014

julia> A
2×2 Matrix{Float64}:
 -0.372281  -1.0
  0.0        5.37228
```
