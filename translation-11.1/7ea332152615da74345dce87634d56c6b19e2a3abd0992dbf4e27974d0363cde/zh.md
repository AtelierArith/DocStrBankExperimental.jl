```
eigvals!(A, B; sortby) -> values
```

与 [`eigvals`](@ref) 相同，但通过覆盖输入 `A`（和 `B`）来节省空间，而不是创建副本。

!!! note
    在调用 `eigvals!` 后，输入矩阵 `A` 和 `B` 将不再包含它们的特征值。它们被用作工作空间。


# 示例

```jldoctest
julia> A = [1. 0.; 0. -1.]
2×2 Matrix{Float64}:
 1.0   0.0
 0.0  -1.0

julia> B = [0. 1.; 1. 0.]
2×2 Matrix{Float64}:
 0.0  1.0
 1.0  0.0

julia> eigvals!(A, B)
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> A
2×2 Matrix{Float64}:
 -0.0  -1.0
  1.0  -0.0

julia> B
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
