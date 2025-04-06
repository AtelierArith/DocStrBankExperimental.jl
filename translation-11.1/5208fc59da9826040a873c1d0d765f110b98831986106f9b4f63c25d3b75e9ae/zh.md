```
cholesky(A, NoPivot(); check = true) -> Cholesky
```

计算稠密对称正定矩阵 `A` 的 Cholesky 分解，并返回一个 [`Cholesky`](@ref) 分解。矩阵 `A` 可以是一个 [`Symmetric`](@ref) 或 [`Hermitian`](@ref) [`AbstractMatrix`](@ref)，或者是一个 *完全* 对称或 Hermitian 的 `AbstractMatrix`。

可以通过 `F.L` 和 `F.U` 从分解 `F` 中获得三角形 Cholesky 因子，其中 `A ≈ F.U' * F.U ≈ F.L * F.L'`。

对于 `Cholesky` 对象，提供以下函数：[`size`](@ref)、[`\`](@ref)、[`inv`](@ref)、[`det`](@ref)、[`logdet`](@ref) 和 [`isposdef`](@ref)。

如果你有一个由于构造中的舍入误差而稍微非 Hermitian 的矩阵 `A`，请在将其传递给 `cholesky` 之前用 `Hermitian(A)` 将其包装，以便将其视为完全 Hermitian。

当 `check = true` 时，如果分解失败，将抛出错误。当 `check = false` 时，检查分解有效性的责任（通过 [`issuccess`](@ref)）在于用户。

# 示例

```jldoctest
julia> A = [4. 12. -16.; 12. 37. -43.; -16. -43. 98.]
3×3 Matrix{Float64}:
   4.0   12.0  -16.0
  12.0   37.0  -43.0
 -16.0  -43.0   98.0

julia> C = cholesky(A)
Cholesky{Float64, Matrix{Float64}}
U factor:
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.U
3×3 UpperTriangular{Float64, Matrix{Float64}}:
 2.0  6.0  -8.0
  ⋅   1.0   5.0
  ⋅    ⋅    3.0

julia> C.L
3×3 LowerTriangular{Float64, Matrix{Float64}}:
  2.0   ⋅    ⋅
  6.0  1.0   ⋅
 -8.0  5.0  3.0

julia> C.L * C.U == A
true
```
