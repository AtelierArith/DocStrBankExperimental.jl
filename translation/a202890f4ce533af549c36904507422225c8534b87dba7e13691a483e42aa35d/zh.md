```
accumulate!(op, B, A; [dims], [init])
```

对 `A` 进行累积操作 `op`，沿着维度 `dims`，将结果存储在 `B` 中。对于向量，提供 `dims` 是可选的。如果给定了关键字参数 `init`，则其值用于初始化累积。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


另请参见 [`accumulate`](@ref), [`cumsum!`](@ref), [`cumprod!`](@ref)。

# 示例

```jldoctest
julia> x = [1, 0, 2, 0, 3];

julia> y = rand(5);

julia> accumulate!(+, y, x);

julia> y
5-element Vector{Float64}:
 1.0
 1.0
 3.0
 3.0
 6.0

julia> A = [1 2 3; 4 5 6];

julia> B = similar(A);

julia> accumulate!(-, B, A, dims=1)
2×3 Matrix{Int64}:
  1   2   3
 -3  -3  -3

julia> accumulate!(*, B, A, dims=2, init=10)
2×3 Matrix{Int64}:
 10   20    60
 40  200  1200
```
