```
values(a::AbstractDict)
```

返回集合中所有值的迭代器。`collect(values(a))` 返回一个值的数组。当值内部存储在哈希表中时，例如 `Dict`，返回的顺序可能会有所不同。但是 `keys(a)`、`values(a)` 和 `pairs(a)` 都会迭代 `a` 并以相同的顺序返回元素。

# 示例

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> collect(values(D))
2-element Vector{Int64}:
 2
 3
```
