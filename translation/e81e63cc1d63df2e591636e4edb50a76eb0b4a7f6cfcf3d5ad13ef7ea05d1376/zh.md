```
dropzeros(x::AbstractCompressedVector)
```

生成 `x` 的副本并从该副本中移除数值零。

有关就地版本和算法信息，请参见 [`dropzeros!`](@ref)。

# 示例

```jldoctest
julia> A = sparsevec([1, 2, 3], [1.0, 0.0, 1.0])
3-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  1.0
  [2]  =  0.0
  [3]  =  1.0

julia> dropzeros(A)
3-element SparseVector{Float64, Int64} with 2 stored entries:
  [1]  =  1.0
  [3]  =  1.0
```
