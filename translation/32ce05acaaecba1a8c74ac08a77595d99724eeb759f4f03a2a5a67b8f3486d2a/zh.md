```
sortperm(A; alg::Algorithm=DEFAULT_UNSTABLE, lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward, [dims::Integer])
```

返回一个排列向量或数组 `I`，使得 `A[I]` 在给定维度上按排序顺序排列。如果 `A` 有多个维度，则必须指定 `dims` 关键字参数。排序顺序使用与 [`sort!`](@ref) 相同的关键字指定。即使排序算法是不稳定的，排列也保证是稳定的：相等元素的索引将按升序出现。

另请参见 [`sortperm!`](@ref)、[`partialsortperm`](@ref)、[`invperm`](@ref)、[`indexin`](@ref)。要对数组的切片进行排序，请参阅 [`sortslices`](@ref)。

!!! compat "Julia 1.9"
    接受 `dims` 的方法至少需要 Julia 1.9。


# 示例

```jldoctest
julia> v = [3, 1, 2];

julia> p = sortperm(v)
3-element Vector{Int64}:
 2
 3
 1

julia> v[p]
3-element Vector{Int64}:
 1
 2
 3

julia> A = [8 7; 5 6]
2×2 Matrix{Int64}:
 8  7
 5  6

julia> sortperm(A, dims = 1)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> sortperm(A, dims = 2)
2×2 Matrix{Int64}:
 3  1
 2  4
```
