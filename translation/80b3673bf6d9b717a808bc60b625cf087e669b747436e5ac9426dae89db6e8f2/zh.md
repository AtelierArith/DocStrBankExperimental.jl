```
eigen(A; permute::Bool=true, scale::Bool=true, sortby) -> Eigen
```

计算 `A` 的特征值分解，返回一个 [`Eigen`](@ref) 分解对象 `F`，该对象包含特征值在 `F.values` 中，特征向量在矩阵 `F.vectors` 的列中。这对应于求解形式为 `Ax =  λx` 的特征值问题，其中 `A` 是一个矩阵，`x` 是一个特征向量，`λ` 是一个特征值。(`k`th 特征向量可以通过切片 `F.vectors[:, k]` 获得。)

迭代分解会产生组件 `F.values` 和 `F.vectors`。

以下函数可用于 `Eigen` 对象：[`inv`](@ref)、[`det`](@ref) 和 [`isposdef`](@ref)。

对于一般的非对称矩阵，可以指定在特征向量计算之前如何平衡矩阵。选项 `permute=true` 会对矩阵进行置换，使其更接近上三角形，`scale=true` 会通过其对角元素缩放矩阵，使行和列在范数上更为相等。默认情况下，这两个选项均为 `true`。

默认情况下，特征值和特征向量按 `(real(λ),imag(λ))` 进行字典序排序。可以将不同的比较函数 `by(λ)` 传递给 `sortby`，或者可以传递 `sortby=nothing` 以保持特征值的任意顺序。一些特殊的矩阵类型（例如 [`Diagonal`](@ref) 或 [`SymTridiagonal`](@ref)）可能会实现自己的排序约定，并不接受 `sortby` 关键字。

# 示例

```jldoctest
julia> F = eigen([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
3-element Vector{Float64}:
  1.0
  3.0
 18.0
vectors:
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> F.values
3-element Vector{Float64}:
  1.0
  3.0
 18.0

julia> F.vectors
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> vals, vecs = F; # 通过迭代解构

julia> vals == F.values && vecs == F.vectors
true
```
