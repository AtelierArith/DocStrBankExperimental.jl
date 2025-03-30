```
sparsevec(I, V, [m, combine])
```

创建一个长度为 `m` 的稀疏向量 `S`，使得 `S[I[k]] = V[k]`。重复的元素使用 `combine` 函数合并，如果没有提供 `combine` 参数，则默认为 `+`，除非 `V` 的元素是布尔值，在这种情况下 `combine` 默认为 `|`。

# 示例

```jldoctest
julia> II = [1, 3, 3, 5]; V = [0.1, 0.2, 0.3, 0.2];

julia> sparsevec(II, V)
5-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  0.5
  [5]  =  0.2

julia> sparsevec(II, V, 8, -)
8-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  -0.1
  [5]  =  0.2

julia> sparsevec([1, 3, 1, 2, 2], [true, true, false, false, false])
3-element SparseVector{Bool, Int64} with 3 stored entries:
  [1]  =  1
  [2]  =  0
  [3]  =  1
```
