```
eachcol(A::AbstractVecOrMat) <: AbstractVector
```

创建一个 [`ColumnSlices`](@ref) 对象，它是矩阵或向量 `A` 的列向量。列切片作为 `AbstractVector` 视图返回。

对于反向操作，请参见 [`stack`](@ref)`(cols)` 或 `reduce(`[`hcat`](@ref)`, cols)`。

另请参见 [`eachrow`](@ref)、[`eachslice`](@ref) 和 [`mapslices`](@ref)。

!!! compat "Julia 1.1"
    此函数至少需要 Julia 1.1。


!!! compat "Julia 1.9"
    在 Julia 1.9 之前，这返回一个迭代器。


# 示例

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> s = eachcol(a)
2-element ColumnSlices{Matrix{Int64}, Tuple{Base.OneTo{Int64}}, SubArray{Int64, 1, Matrix{Int64}, Tuple{Base.Slice{Base.OneTo{Int64}}, Int64}, true}}:
 [1, 3]
 [2, 4]

julia> s[1]
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3
```
