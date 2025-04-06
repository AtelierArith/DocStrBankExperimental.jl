```
transpose(A)
```

懒转置。修改返回的对象应适当地修改 `A`。通常，但并不总是，返回 `Transpose(A)`，其中 `Transpose` 是一个懒转置包装器。请注意，此操作是递归的。

此操作旨在用于线性代数 - 有关一般数据操作，请参见 [`permutedims`](@ref Base.permutedims)，该操作是非递归的。

# 示例

```jldoctest
julia> A = [3 2; 0 0]
2×2 Matrix{Int64}:
 3  2
 0  0

julia> B = transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 3  0
 2  0

julia> B isa Transpose
true

julia> transpose(B) === A # 转置的转置解包父对象
true

julia> Transpose(B) # 然而，构造函数始终包装其参数
2×2 transpose(transpose(::Matrix{Int64})) with eltype Int64:
 3  2
 0  0

julia> B[1,2] = 4; # 修改 B 将自动修改 A

julia> A
2×2 Matrix{Int64}:
 3  2
 4  0
```

对于复数矩阵，`adjoint` 操作等同于共轭转置。

```jldoctest
julia> A = reshape([Complex(x, x) for x in 1:4], 2, 2)
2×2 Matrix{Complex{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> adjoint(A) == conj(transpose(A))
true
```

`AbstractVector` 的 `transpose` 是一个行向量：

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> transpose(v) # 返回一个行向量
1×3 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3

julia> transpose(v) * v # 计算点积
14
```

对于矩阵的矩阵，单个块是递归操作的：

```jldoctest
julia> C = [1 3; 2 4]
2×2 Matrix{Int64}:
 1  3
 2  4

julia> D = reshape([C, 2C, 3C, 4C], 2, 2) # 构造一个块矩阵
2×2 Matrix{Matrix{Int64}}:
 [1 3; 2 4]  [3 9; 6 12]
 [2 6; 4 8]  [4 12; 8 16]

julia> transpose(D) # 块被递归转置
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 2; 3 4]   [2 4; 6 8]
 [3 6; 9 12]  [4 8; 12 16]
```
