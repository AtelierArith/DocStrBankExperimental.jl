```
permutedims(A::AbstractArray, perm)
permutedims(A::AbstractMatrix)
```

对数组 `A` 的维度（轴）进行排列。`perm` 是一个元组或向量，包含 `ndims(A)` 个整数，指定排列顺序。

如果 `A` 是一个二维数组（[`AbstractMatrix`](@ref)），则 `perm` 默认为 `(2,1)`，交换 `A` 的两个轴（矩阵的行和列）。这与 [`transpose`](@ref) 不同，因为该操作不是递归的，这对于非数值值的数组（递归的 `transpose` 会抛出错误）和/或不表示线性算子的二维数组尤其有用。

对于一维数组，请参见 [`permutedims(v::AbstractVector)`](@ref)，它返回一个1行的“矩阵”。

另请参见 [`permutedims!`](@ref)，[`PermutedDimsArray`](@ref)，[`transpose`](@ref)，[`invperm`](@ref)。

# 示例

## 二维数组：

与 `transpose` 不同，`permutedims` 可以用于交换任意非数值元素的二维数组的行和列，例如字符串：

```jldoctest
julia> A = ["a" "b" "c"
            "d" "e" "f"]
2×3 Matrix{String}:
 "a"  "b"  "c"
 "d"  "e"  "f"

julia> permutedims(A)
3×2 Matrix{String}:
 "a"  "d"
 "b"  "e"
 "c"  "f"
```

而且 `permutedims` 对于其元素本身是数值矩阵的矩阵产生的结果与 `transpose` 不同：

```jldoctest; setup = :(using LinearAlgebra)
julia> a = [1 2; 3 4];

julia> b = [5 6; 7 8];

julia> c = [9 10; 11 12];

julia> d = [13 14; 15 16];

julia> X = [[a] [b]; [c] [d]]
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]     [5 6; 7 8]
 [9 10; 11 12]  [13 14; 15 16]

julia> permutedims(X)
2×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [9 10; 11 12]
 [5 6; 7 8]  [13 14; 15 16]

julia> transpose(X)
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [9 11; 10 12]
 [5 7; 6 8]  [13 15; 14 16]
```

## 多维数组

```jldoctest
julia> A = reshape(Vector(1:8), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> perm = (3, 1, 2); # 将最后一个维度放在最前面

julia> B = permutedims(A, perm)
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 5  6

[:, :, 2] =
 3  4
 7  8

julia> A == permutedims(B, invperm(perm)) # 逆排列
true
```

对于 `B = permutedims(A, perm)` 的每个维度 `i`，其对应的 `A` 的维度将是 `perm[i]`。这意味着等式 `size(B, i) == size(A, perm[i])` 成立。

```jldoctest
julia> A = randn(5, 7, 11, 13);

julia> perm = [4, 1, 3, 2];

julia> B = permutedims(A, perm);

julia> size(B)
(13, 5, 11, 7)

julia> size(A)[perm] == ans
true
```
