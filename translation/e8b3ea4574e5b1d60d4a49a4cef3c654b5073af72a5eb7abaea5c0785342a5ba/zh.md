```
values(iterator)
```

对于具有键和值的迭代器或集合，返回一个值的迭代器。此函数默认简单地返回其参数，因为一般迭代器的元素通常被视为其“值”。

# 示例

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> values(d)
ValueIterator for a Dict{String, Int64} with 2 entries. Values:
  2
  1

julia> values([2])
1-element Vector{Int64}:
 2
```
