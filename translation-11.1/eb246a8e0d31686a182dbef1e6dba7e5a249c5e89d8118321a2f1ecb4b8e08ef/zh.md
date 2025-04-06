```
minimum(A::AbstractArray; dims)
```

计算给定维度上数组的最小值。另请参见 [`min(a,b)`](@ref) 函数，该函数用于获取两个或多个参数的最小值，可以通过 `min.(a,b)` 元素级地应用于数组。

另请参见: [`minimum!`](@ref), [`extrema`](@ref), [`findmin`](@ref), [`argmin`](@ref)。

# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum(A, dims=1)
1×2 Matrix{Int64}:
 1  2

julia> minimum(A, dims=2)
2×1 Matrix{Int64}:
 1
 3
```
