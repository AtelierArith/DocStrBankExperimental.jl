```
sort(A; dims::Integer, alg::Algorithm=defalg(A), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

沿给定维度对多维数组 `A` 进行排序。有关可能的关键字参数的描述，请参见 [`sort!`](@ref)。

要对数组的切片进行排序，请参考 [`sortslices`](@ref)。

# 示例

```jldoctest
julia> A = [4 3; 1 2]
2×2 Matrix{Int64}:
 4  3
 1  2

julia> sort(A, dims = 1)
2×2 Matrix{Int64}:
 1  2
 4  3

julia> sort(A, dims = 2)
2×2 Matrix{Int64}:
 3  4
 1  2
```
