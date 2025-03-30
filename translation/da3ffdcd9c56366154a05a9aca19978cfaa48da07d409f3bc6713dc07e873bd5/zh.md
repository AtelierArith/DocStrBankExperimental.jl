```
mean(f, A::AbstractArray; dims)
```

将函数 `f` 应用到数组 `A` 的每个元素，并在维度 `dims` 上取平均值。

!!! compat "Julia 1.3"
    此方法需要至少 Julia 1.3。


```jldoctest
julia> using Statistics

julia> mean(√, [1, 2, 3])
1.3820881233139908

julia> mean([√1, √2, √3])
1.3820881233139908

julia> mean(√, [1 2 3; 4 5 6], dims=2)
2×1 Matrix{Float64}:
 1.3820881233139908
 2.2285192400943226
```
