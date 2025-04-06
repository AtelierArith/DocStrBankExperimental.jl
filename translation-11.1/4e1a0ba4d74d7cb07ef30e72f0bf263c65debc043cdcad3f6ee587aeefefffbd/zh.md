```
ntuple(f, n::Integer)
```

创建一个长度为 `n` 的元组，计算每个元素为 `f(i)`，其中 `i` 是元素的索引。

# 示例

```jldoctest
julia> ntuple(i -> 2*i, 4)
(2, 4, 6, 8)
```
