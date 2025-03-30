```
Diagonal(V::AbstractVector)
```

构造一个以 `V` 为对角线的惰性矩阵。

另请参见 [`UniformScaling`](@ref) 用于惰性单位矩阵 `I`，[`diagm`](@ref) 用于创建稠密矩阵，以及 [`diag`](@ref) 用于提取对角元素。

# 示例

```jldoctest
julia> d = Diagonal([1, 10, 100])
3×3 Diagonal{Int64, Vector{Int64}}:
 1   ⋅    ⋅
 ⋅  10    ⋅
 ⋅   ⋅  100

julia> diagm([7, 13])
2×2 Matrix{Int64}:
 7   0
 0  13

julia> ans + I
2×2 Matrix{Int64}:
 8   0
 0  14

julia> I(2)
2×2 Diagonal{Bool, Vector{Bool}}:
 1  ⋅
 ⋅  1
```

!!! 注意     一列矩阵不会被视为向量，而是调用方法 `Diagonal(A::AbstractMatrix)`，该方法提取 1 元素 `diag(A)`：

```jldoctest
julia> A = transpose([7.0 13.0])
2×1 transpose(::Matrix{Float64}) with eltype Float64:
  7.0
 13.0

julia> Diagonal(A)
1×1 Diagonal{Float64, Vector{Float64}}:
 7.0
```
