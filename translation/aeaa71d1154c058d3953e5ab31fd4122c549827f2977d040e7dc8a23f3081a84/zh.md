```
rmul!(A, B)
```

计算矩阵-矩阵乘积 $AB$，覆盖 `A`，并返回结果。这里，`B` 必须是特殊矩阵类型，例如 [`Diagonal`](@ref)、[`UpperTriangular`](@ref) 或 [`LowerTriangular`](@ref)，或某种正交类型，参见 [`QR`](@ref)。

# 示例

```jldoctest
julia> A = [0 1; 1 0];

julia> B = UpperTriangular([1 2; 0 3]);

julia> rmul!(A, B);

julia> A
2×2 Matrix{Int64}:
 0  3
 1  2

julia> A = [1.0 2.0; 3.0 4.0];

julia> F = qr([0 1; -1 0]);

julia> rmul!(A, F.Q)
2×2 Matrix{Float64}:
 2.0  1.0
 4.0  3.0
```
