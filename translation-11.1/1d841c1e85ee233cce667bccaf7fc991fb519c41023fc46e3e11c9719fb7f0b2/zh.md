```
pairs(collection)
```

返回一个迭代器，遍历任何将一组键映射到一组值的集合的 `key => value` 对。这包括数组，其中键是数组索引。当条目内部存储在哈希表中时，例如 `Dict` 的情况，返回的顺序可能会有所不同。但是 `keys(a)`、`values(a)` 和 `pairs(a)` 都会遍历 `a` 并以相同的顺序返回元素。

# 示例

```jldoctest
julia> a = Dict(zip(["a", "b", "c"], [1, 2, 3]))
Dict{String, Int64} with 3 entries:
  "c" => 3
  "b" => 2
  "a" => 1

julia> pairs(a)
Dict{String, Int64} with 3 entries:
  "c" => 3
  "b" => 2
  "a" => 1

julia> foreach(println, pairs(["a", "b", "c"]))
1 => "a"
2 => "b"
3 => "c"

julia> (;a=1, b=2, c=3) |> pairs |> collect
3-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
 :c => 3

julia> (;a=1, b=2, c=3) |> collect
3-element Vector{Int64}:
 1
 2
 3
```
