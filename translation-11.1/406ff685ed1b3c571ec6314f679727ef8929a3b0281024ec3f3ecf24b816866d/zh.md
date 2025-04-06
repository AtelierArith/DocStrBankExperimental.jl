```
CartesianIndex(i, j, k...)   -> I
CartesianIndex((i, j, k...)) -> I
```

创建一个多维索引 `I`，可以用于索引多维数组 `A`。特别地，`A[I]` 等价于 `A[i,j,k...]`。可以自由混合整数和 `CartesianIndex` 索引；例如，`A[Ipre, i, Ipost]`（其中 `Ipre` 和 `Ipost` 是 `CartesianIndex` 索引，`i` 是 `Int`）在编写沿着任意维度的数组的算法时可以是一个有用的表达式。

`CartesianIndex` 有时由 [`eachindex`](@ref) 生成，并且在使用显式的 [`CartesianIndices`](@ref) 进行迭代时总是会生成。

`I::CartesianIndex` 被视为 `broadcast` 的“标量”（而不是容器）。为了迭代 `CartesianIndex` 的组件，可以使用 `Tuple(I)` 将其转换为元组。

# 示例

```jldoctest
julia> A = reshape(Vector(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[CartesianIndex((1, 1, 1, 1))]
1

julia> A[CartesianIndex((1, 1, 1, 2))]
9

julia> A[CartesianIndex((1, 1, 2, 1))]
5
```

!!! compat "Julia 1.10"
    将 `CartesianIndex` 作为 `broadcast` 的“标量”需要 Julia 1.10；在之前的版本中，请使用 `Ref(I)`。

