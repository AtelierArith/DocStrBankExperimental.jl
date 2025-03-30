```
copy(A::Transpose)
copy(A::Adjoint)
```

急切地评估惰性矩阵的转置/伴随。请注意，转置是递归地应用于元素的。

此操作旨在用于线性代数 - 有关一般数据操作，请参见 [`permutedims`](@ref Base.permutedims)，该操作是非递归的。

# 示例

```jldoctest
julia> A = [1 2im; -3im 4]
2×2 Matrix{Complex{Int64}}:
 1+0im  0+2im
 0-3im  4+0im

julia> T = transpose(A)
2×2 transpose(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 1+0im  0-3im
 0+2im  4+0im

julia> copy(T)
2×2 Matrix{Complex{Int64}}:
 1+0im  0-3im
 0+2im  4+0im
```
