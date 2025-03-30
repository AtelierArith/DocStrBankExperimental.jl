```
PersistentDict
```

`PersistentDict` 是一个实现为哈希数组映射前缀树的字典，适用于需要持久性的情况，每个操作返回一个与之前不同的新字典，但其底层实现是空间高效的，并且可能在多个独立字典之间共享存储。

!!! note
    它的行为类似于 IdDict。


```julia
PersistentDict(KV::Pair)
```

# 示例

```jldoctest
julia> dict = Base.PersistentDict(:a=>1)
Base.PersistentDict{Symbol, Int64} with 1 entry:
  :a => 1

julia> dict2 = Base.delete(dict, :a)
Base.PersistentDict{Symbol, Int64}()

julia> dict3 = Base.PersistentDict(dict, :a=>2)
Base.PersistentDict{Symbol, Int64} with 1 entry:
  :a => 2
```
