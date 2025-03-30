```
map(f, A::AbstractArray...) -> N-array
```

当作用于具有相同 [`ndims`](@ref) 的多维数组时，它们必须具有相同的 [`axes`](@ref)，结果也将如此。

另请参见 [`broadcast`](@ref)，它允许不匹配的大小。

# 示例

```
julia> map(//, [1 2; 3 4], [4 3; 2 1])
2×2 Matrix{Rational{Int64}}:
 1//4  2//3
 3//2  4//1

julia> map(+, [1 2; 3 4], zeros(2,1))
ERROR: DimensionMismatch

julia> map(+, [1 2; 3 4], [1,10,100,1000], zeros(3,1))  # 迭代直到第三个耗尽
3-element Vector{Float64}:
   2.0
  13.0
 102.0
```
