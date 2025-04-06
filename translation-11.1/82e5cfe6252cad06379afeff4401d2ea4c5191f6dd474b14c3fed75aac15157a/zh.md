```
keepat!(a::Vector, m::AbstractVector{Bool})
keepat!(a::BitVector, m::AbstractVector{Bool})
```

逻辑索引的就地版本 `a = a[m]`。也就是说，在长度相等的向量 `a` 和 `m` 上使用 `keepat!(a, m)` 将移除 `a` 中所有对应索引的 `m` 为 `false` 的元素。

# 示例

```jldoctest
julia> a = [:a, :b, :c];

julia> keepat!(a, [true, false, true])
2-element Vector{Symbol}:
 :a
 :c

julia> a
2-element Vector{Symbol}:
 :a
 :c
```
