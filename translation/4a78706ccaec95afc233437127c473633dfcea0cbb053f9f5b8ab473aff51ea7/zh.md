```
UnitLowerTriangular(A::AbstractMatrix)
```

构造矩阵 `A` 的 `UnitLowerTriangular` 视图。这样的视图在其对角线上具有 `A` 的 [`eltype`](@ref) 的 [`oneunit`](@ref)。

# 示例

```jldoctest
julia> A = [1.0 2.0 3.0; 4.0 5.0 6.0; 7.0 8.0 9.0]
3×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
 7.0  8.0  9.0

julia> UnitLowerTriangular(A)
3×3 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0   ⋅    ⋅
 4.0  1.0   ⋅
 7.0  8.0  1.0
```
