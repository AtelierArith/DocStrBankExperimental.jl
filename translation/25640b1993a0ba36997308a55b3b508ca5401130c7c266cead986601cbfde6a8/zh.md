```
sparsevec(d::Dict, [m])
```

创建一个长度为 `m` 的稀疏向量，其中非零索引是字典中的键，非零值是字典中的值。

# 示例

```jldoctest
julia> sparsevec(Dict(1 => 3, 2 => 2))
2-element SparseVector{Int64, Int64} with 2 stored entries:
  [1]  =  3
  [2]  =  2
```
