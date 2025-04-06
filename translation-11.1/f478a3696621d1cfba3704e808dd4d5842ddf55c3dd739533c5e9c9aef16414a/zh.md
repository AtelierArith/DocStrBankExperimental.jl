```
getindex(A, inds...)
```

返回由索引 `inds` 选择的数组 `A` 的子集。

每个索引可以是任何 [支持的索引类型](@ref man-supported-index-types)，例如 [`Integer`](@ref)、[`CartesianIndex`](@ref)、[范围](@ref Base.AbstractRange) 或 [支持的索引数组](@ref man-multi-dim-arrays)。可以使用一个 [:](@ref Base.Colon) 来选择特定维度上的所有元素，布尔数组（例如 `Array{Bool}` 或 [`BitArray`](@ref)）可以用来过滤对应索引为 `true` 的元素。

当 `inds` 选择多个元素时，此函数返回一个新分配的数组。要在不复制的情况下索引多个元素，请改用 [`view`](@ref)。

有关详细信息，请参见手册中的 [数组索引](@ref man-array-indexing) 部分。

# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> getindex(A, 1)
1

julia> getindex(A, [2, 1])
2-element Vector{Int64}:
 3
 1

julia> getindex(A, 2:4)
3-element Vector{Int64}:
 3
 2
 4

julia> getindex(A, 2, 1)
3

julia> getindex(A, CartesianIndex(2, 1))
3

julia> getindex(A, :, 2)
2-element Vector{Int64}:
 2
 4

julia> getindex(A, 2, :)
2-element Vector{Int64}:
 3
 4

julia> getindex(A, A .> 2)
2-element Vector{Int64}:
 3
 4
```
