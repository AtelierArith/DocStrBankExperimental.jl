```
Dict([itr])
```

`Dict{K,V}()` 构造一个哈希表，键的类型为 `K`，值的类型为 `V`。键通过 [`isequal`](@ref) 进行比较，并通过 [`hash`](@ref) 进行哈希。

给定一个可迭代的单一参数，构造一个 [`Dict`](@ref)，其键值对来自于参数生成的 2 元组 `(key,value)`。

# 示例

```jldoctest
julia> Dict([("A", 1), ("B", 2)])
Dict{String, Int64} with 2 entries:
  "B" => 2
  "A" => 1
```

或者，可以传递一系列成对的参数。

```jldoctest
julia> Dict("A"=>1, "B"=>2)
Dict{String, Int64} with 2 entries:
  "B" => 2
  "A" => 1
```

!!! warning
    键允许是可变的，但如果你确实修改了存储的键，哈希表可能会变得内部不一致，在这种情况下，`Dict` 将无法正常工作。如果需要修改键，[`IdDict`](@ref) 可以作为替代方案。

