```
Tridiagonal(dl::V, d::V, du::V) where V <: AbstractVector
```

从第一个下对角线、对角线和第一个上对角线分别构造一个三对角矩阵。结果是 `Tridiagonal` 类型，并提供高效的专用线性求解器，但可以通过 [`convert(Array, _)`](@ref)（或简写为 `Array(_)`）转换为常规矩阵。`dl` 和 `du` 的长度必须比 `d` 的长度少一。

!!! note
    下对角线 `dl` 和上对角线 `du` 不能相互别名。如果检测到别名，构造函数将使用 `du` 的副本作为其参数。


# 示例

```jldoctest
julia> dl = [1, 2, 3];

julia> du = [4, 5, 6];

julia> d = [7, 8, 9, 0];

julia> Tridiagonal(dl, d, du)
4×4 Tridiagonal{Int64, Vector{Int64}}:
 7  4  ⋅  ⋅
 1  8  5  ⋅
 ⋅  2  9  6
 ⋅  ⋅  3  0
```
