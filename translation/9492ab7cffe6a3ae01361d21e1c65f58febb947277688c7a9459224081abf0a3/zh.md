```
eigen(A, B; sortby) -> GeneralizedEigen
```

计算 `A` 和 `B` 的广义特征值分解，返回一个 [`GeneralizedEigen`](@ref) 分解对象 `F`，其中包含广义特征值在 `F.values` 中，广义特征向量在矩阵 `F.vectors` 的列中。这对应于求解形式为 `Ax =  λBx` 的广义特征值问题，其中 `A, B` 是矩阵，`x` 是特征向量，`λ` 是特征值。(`k`th 广义特征向量可以通过切片 `F.vectors[:, k]` 获得。)

迭代分解会产生组件 `F.values` 和 `F.vectors`。

默认情况下，特征值和特征向量按 `(real(λ),imag(λ))` 进行字典序排序。可以将不同的比较函数 `by(λ)` 传递给 `sortby`，或者可以传递 `sortby=nothing` 以保持特征值的任意顺序。

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

julia> F = eigen(A, B);

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # 通过迭代解构

julia> vals == F.values && vecs == F.vectors
true
```
