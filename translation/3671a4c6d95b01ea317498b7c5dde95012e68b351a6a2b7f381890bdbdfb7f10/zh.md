```
lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC; check=true, reuse_symbolic=true, q=nothing) -> F::UmfpackLU
```

计算稀疏矩阵 `A` 的 LU 分解，重用已存在的 LU 分解中存储的符号分解 `F`。除非将 `reuse_symbolic` 设置为 false，否则稀疏矩阵 `A` 必须具有与用于创建 LU 分解 `F` 的矩阵相同的非零模式，否则会抛出错误。如果 `A` 和 `F` 的大小不同，则所有向量将相应地调整大小。

当 `check = true` 时，如果分解失败，将抛出错误。当 `check = false` 时，检查分解有效性的责任（通过 [`issuccess`](@ref)）由用户承担。

置换 `q` 可以是一个置换向量或 `nothing`。如果未提供置换向量或 `q` 为 `nothing`，则使用 UMFPACK 的默认值。如果置换不是基于零的，则会制作一个基于零的副本。

另见 [`lu`](@ref)

!!! note
    `lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC)` 使用的是 SuiteSparse 中的 UMFPACK 库。由于该库仅支持具有 [`Float64`](@ref) 或 `ComplexF64` 元素的稀疏矩阵，因此 `lu!` 将自动将类型转换为 LU 分解所设置的类型或适当的 `SparseMatrixCSC{ComplexF64}`。


!!! compat "Julia 1.5"
    `UmfpackLU` 的 `lu!` 至少需要 Julia 1.5。


# 示例

```jldoctest
julia> A = sparse(Float64[1.0 2.0; 0.0 3.0]);

julia> F = lu(A);

julia> B = sparse(Float64[1.0 1.0; 0.0 1.0]);

julia> lu!(F, B);

julia> F \ ones(2)
2-element Vector{Float64}:
 0.0
 1.0
```
