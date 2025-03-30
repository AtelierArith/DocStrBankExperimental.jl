```
sort!(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

沿维度 `dims` 对多维数组 `A` 进行排序。有关可能的关键字参数的描述，请参见一维版本的 [`sort!`](@ref)。

要对数组的切片进行排序，请参考 [`sortslices`](@ref)。

!!! compat "Julia 1.1"
    此函数至少需要 Julia 1.1。


# 示例

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort!(A, dims = 1); A
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort!(A, dims = 2); A
2×2 Matrix{Int64}:
 1  2
 3  4
```
