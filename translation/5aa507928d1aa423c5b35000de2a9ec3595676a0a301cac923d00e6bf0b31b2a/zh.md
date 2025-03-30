```
median(A::AbstractArray; dims)
```

计算数组在给定维度上的中位数。

# 示例

```jldoctest
julia> using Statistics

julia> median([1 2; 3 4], dims=1)
1×2 Matrix{Float64}:
 2.0  3.0
```
