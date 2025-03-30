```
Cholesky <: Factorization
```

稠密对称/厄米正定矩阵 `A` 的 Cholesky 分解的矩阵分解类型。这是 [`cholesky`](@ref) 的返回类型，对应的矩阵分解函数。

可以通过 `F::Cholesky` 的分解获得三角形 Cholesky 因子，方法是使用 `F.L` 和 `F.U`，其中 `A ≈ F.U' * F.U ≈ F.L * F.L'`。

以下函数可用于 `Cholesky` 对象：[`size`](@ref)、[`\`](@ref)、[`inv`](@ref)、[`det`](@ref)、[`logdet`](@ref) 和 [`isposdef`](@ref)。

迭代分解会产生组件 `L` 和 `U`。

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

julia> l, u = C; # 通过迭代解构

julia> l == C.L && u == C.U
true
```
