```
lmul!(A, B)
```

计算矩阵-矩阵乘积 $AB$，覆盖 `B`，并返回结果。这里，`A` 必须是特殊矩阵类型，例如 [`Diagonal`](@ref)、[`UpperTriangular`](@ref) 或 [`LowerTriangular`](@ref)，或某种正交类型，参见 [`QR`](@ref)。

# 示例

```jldoctest
julia> B = [0 1; 1 0];

julia> A = UpperTriangular([1 2; 0 3]);

julia> lmul!(A, B);

julia> B
2×2 Matrix{Int64}:
 2  1
 3  0

julia> B = [1.0 2.0; 3.0 4.0];

julia> F = qr([0 1; -1 0]);

julia> lmul!(F.Q, B)
2×2 Matrix{Float64}:
 3.0  4.0
 1.0  2.0
```
