```
A'
adjoint(A)
```

惰性伴随（共轭转置）。请注意，`adjoint` 是递归地应用于元素的。

对于数字类型，`adjoint` 返回复共轭，因此对于实数来说，它等同于恒等函数。

此操作旨在用于线性代数 - 有关一般数据操作，请参见 [`permutedims`](@ref Base.permutedims)。

# 示例

```jldoctest
julia> A = [3+2im 9+2im; 0  0]
2×2 矩阵{复数{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> B = A' # 等同于 adjoint(A)
2×2 adjoint(::矩阵{复数{Int64}}) 具有元素类型 复数{Int64}:
 3-2im  0+0im
 9-2im  0+0im

julia> B isa Adjoint
true

julia> adjoint(B) === A # 伴随的伴随解开父级
true

julia> Adjoint(B) # 然而，构造函数总是包装其参数
2×2 adjoint(adjoint(::矩阵{复数{Int64}})) 具有元素类型 复数{Int64}:
 3+2im  9+2im
 0+0im  0+0im

julia> B[1,2] = 4 + 5im; # 修改 B 将自动修改 A

julia> A
2×2 矩阵{复数{Int64}}:
 3+2im  9+2im
 4-5im  0+0im
```

对于实矩阵，`adjoint` 操作等同于 `transpose`。

```jldoctest
julia> A = reshape([x for x in 1:4], 2, 2)
2×2 矩阵{Int64}:
 1  3
 2  4

julia> A'
2×2 adjoint(::矩阵{Int64}) 具有元素类型 Int64:
 1  2
 3  4

julia> adjoint(A) == transpose(A)
true
```

`AbstractVector` 的伴随是行向量：

```jldoctest
julia> x = [3, 4im]
2-element 向量{复数{Int64}}:
 3 + 0im
 0 + 4im

julia> x'
1×2 adjoint(::向量{复数{Int64}}) 具有元素类型 复数{Int64}:
 3+0im  0-4im

julia> x'x # 计算点积，等同于 x' * x
25 + 0im
```

对于矩阵的矩阵，单个块是递归操作的：

```jldoctest
julia> A = reshape([x + im*x for x in 1:4], 2, 2)
2×2 矩阵{复数{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> C = reshape([A, 2A, 3A, 4A], 2, 2)
2×2 矩阵{矩阵{复数{Int64}}}:
 [1+1im 3+3im; 2+2im 4+4im]  [3+3im 9+9im; 6+6im 12+12im]
 [2+2im 6+6im; 4+4im 8+8im]  [4+4im 12+12im; 8+8im 16+16im]

julia> C'
2×2 adjoint(::矩阵{矩阵{复数{Int64}}}) 具有元素类型 Adjoint{复数{Int64}, 矩阵{复数{Int64}}}:
 [1-1im 2-2im; 3-3im 4-4im]    [2-2im 4-4im; 6-6im 8-8im]
 [3-3im 6-6im; 9-9im 12-12im]  [4-4im 8-8im; 12-12im 16-16im]
```
