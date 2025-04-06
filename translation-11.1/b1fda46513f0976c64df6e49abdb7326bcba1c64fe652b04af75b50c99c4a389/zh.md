```
mean(A::AbstractArray; dims)
```

计算给定维度上的数组均值。

!!! compat "Julia 1.1"
    对于空数组，`mean` 至少需要 Julia 1.1。


# 示例

```jldoctest
julia> using Statistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> mean(A, dims=1)
1×2 Matrix{Float64}:
 2.0  3.0

julia> mean(A, dims=2)
2×1 Matrix{Float64}:
 1.5
 3.5
```
