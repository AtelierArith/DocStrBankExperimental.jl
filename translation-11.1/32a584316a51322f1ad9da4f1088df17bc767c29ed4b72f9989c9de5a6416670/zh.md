```
get!(collection, key, default)
```

返回存储在给定键下的值，如果该键没有映射，则存储 `key => default`，并返回 `default`。

# 示例

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> get!(d, "a", 5)
1

julia> get!(d, "d", 4)
4

julia> d
Dict{String, Int64} with 4 entries:
  "c" => 3
  "b" => 2
  "a" => 1
  "d" => 4
```
