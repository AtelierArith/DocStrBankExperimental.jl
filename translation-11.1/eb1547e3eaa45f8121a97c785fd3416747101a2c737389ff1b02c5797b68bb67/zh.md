```
GeneralizedEigen <: Factorization
```

广义特征值/谱分解的矩阵分解类型，适用于 `A` 和 `B`。这是调用带有两个矩阵参数的 [`eigen`](@ref) 时返回的相应矩阵分解函数的返回类型。

如果 `F::GeneralizedEigen` 是分解对象，则可以通过 `F.values` 获取特征值，通过矩阵 `F.vectors` 的列获取特征向量。（第 `k` 个特征向量可以通过切片 `F.vectors[:, k]` 获取。）

迭代分解会产生组件 `F.values` 和 `F.vectors`。

# 示例

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> F = eigen(A, B)
GeneralizedEigen{ComplexF64, ComplexF64, Matrix{ComplexF64}, Vector{ComplexF64}}
values:
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im
vectors:
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # destructuring via iteration

julia> vals == F.values && vecs == F.vectors
true
```
