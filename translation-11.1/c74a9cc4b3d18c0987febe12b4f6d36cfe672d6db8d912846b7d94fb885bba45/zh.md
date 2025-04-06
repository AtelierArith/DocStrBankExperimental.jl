```
SymTridiagonal(dv::V, ev::V) where V <: AbstractVector
```

从对角线（`dv`）和第一条下/上对角线（`ev`）构造一个对称三对角矩阵。结果是 `SymTridiagonal` 类型，并提供高效的专用特征值求解器，但可以通过 [`convert(Array, _)`](@ref)（或简写为 `Array(_)`）转换为常规矩阵。

对于 `SymTridiagonal` 块矩阵，`dv` 的元素被对称化。参数 `ev` 被解释为上对角线。下对角线的块是相应上对角线块的（物化）转置。

# 示例

```jldoctest
julia> dv = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-element Vector{Int64}:
 7
 8
 9

julia> SymTridiagonal(dv, ev)
4×4 SymTridiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 7  2  8  ⋅
 ⋅  8  3  9
 ⋅  ⋅  9  4

julia> A = SymTridiagonal(fill([1 2; 3 4], 3), fill([1 2; 3 4], 2));

julia> A[1,1]
2×2 Symmetric{Int64, Matrix{Int64}}:
 1  2
 2  4

julia> A[1,2]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> A[2,1]
2×2 Matrix{Int64}:
 1  3
 2  4
```
