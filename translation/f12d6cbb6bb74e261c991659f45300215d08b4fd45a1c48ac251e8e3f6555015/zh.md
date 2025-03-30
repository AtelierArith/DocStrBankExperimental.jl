```
setindex!(collection, value, key...)
```

在集合中以给定的键或索引存储给定的值。语法 `a[i,j,...] = x` 被编译器转换为 `(setindex!(a, x, i, j, ...); x)`。

# 示例

```jldoctest
julia> a = Dict("a"=>1)
Dict{String, Int64} with 1 entry:
  "a" => 1

julia> setindex!(a, 2, "b")
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1
```
