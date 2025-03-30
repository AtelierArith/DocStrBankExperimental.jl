```
pop!(collection, key[, default])
```

如果 `key` 存在于 `collection` 中，则删除并返回该映射，否则返回 `default`，如果未指定 `default` 则抛出错误。

# 示例

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> pop!(d, "a")
1

julia> pop!(d, "d")
ERROR: KeyError: key "d" not found
Stacktrace:
[...]

julia> pop!(d, "e", 4)
4
```
