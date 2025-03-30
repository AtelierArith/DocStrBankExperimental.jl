```
delete!(collection, key)
```

删除集合中给定键的映射（如果存在），并返回集合。

# 示例

```jldoctest
julia> d = Dict("a"=>1, "b"=>2)
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1

julia> delete!(d, "b")
Dict{String, Int64} with 1 entry:
  "a" => 1

julia> delete!(d, "b") # d 保持不变
Dict{String, Int64} with 1 entry:
  "a" => 1
```
