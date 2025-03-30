```
eachslice(A::AbstractArray; dims, drop=true)
```

创建一个 [`Slices`](@ref) 对象，该对象是 `A` 的 `dims` 维度上的切片数组，返回选择 `A` 中其他维度所有数据的视图。`dims` 可以是一个整数或一个整数元组。

如果 `drop = true`（默认值），外部的 `Slices` 将丢弃内部维度，维度的顺序将与 `dims` 中的顺序匹配。如果 `drop = false`，则 `Slices` 将具有与基础数组相同的维度，内部维度的大小为 1。

请参见 [`stack`](@ref)`(slices; dims)` 以获取 `eachslice(A; dims::Integer)` 的逆操作。

另请参见 [`eachrow`](@ref)、[`eachcol`](@ref)、[`mapslices`](@ref) 和 [`selectdim`](@ref)。

!!! compat "Julia 1.1"
    此函数至少需要 Julia 1.1。


!!! compat "Julia 1.9"
    在 Julia 1.9 之前，这返回一个迭代器，并且仅支持单个维度 `dims`。


# 示例

```jldoctest
julia> m = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> s = eachslice(m, dims=1)
3-element RowSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]

julia> s[1]
3-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2
 3

julia> eachslice(m, dims=1, drop=false)
3×1 Slices{Matrix{Int64}, Tuple{Int64, Colon}, Tuple{Base.OneTo{Int64}, Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Int64, Base.Slice{Base.OneTo{Int64}}}, true}, 2}:
 [1, 2, 3]
 [4, 5, 6]
 [7, 8, 9]
```
