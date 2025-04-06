```
diff(A::AbstractVector)
diff(A::AbstractArray; dims::Integer)
```

在向量或多维数组 `A` 上的有限差分算子。在后者的情况下，需要通过 `dims` 关键字参数指定操作的维度。

!!! compat "Julia 1.1"
    对于维度高于 2 的数组，`diff` 至少需要 Julia 1.1。


# 示例

```jldoctest
julia> a = [2 4; 6 16]
2×2 Matrix{Int64}:
 2   4
 6  16

julia> diff(a, dims=2)
2×1 Matrix{Int64}:
  2
 10

julia> diff(vec(a))
3-element Vector{Int64}:
  4
 -2
 12
```
