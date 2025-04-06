```
isposdef!(A) -> Bool
```

测试一个矩阵是否为正定（和厄米）通过尝试对 `A` 进行 Cholesky 分解，并在此过程中覆盖 `A`。另见 [`isposdef`](@ref)。

# 示例

```jldoctest
julia> A = [1. 2.; 2. 50.];

julia> isposdef!(A)
true

julia> A
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  6.78233
```
