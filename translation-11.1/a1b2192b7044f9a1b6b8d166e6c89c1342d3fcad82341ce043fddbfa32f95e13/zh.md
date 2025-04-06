```
isposdef(A) -> Bool
```

测试一个矩阵是否是正定的（和厄米的），通过尝试对 `A` 进行 Cholesky 分解。

另见 [`isposdef!`](@ref), [`cholesky`](@ref).

# 示例

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> isposdef(A)
true
```
