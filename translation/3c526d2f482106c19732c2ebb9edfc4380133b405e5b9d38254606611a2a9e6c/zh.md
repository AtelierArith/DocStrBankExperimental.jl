```
get(collection, key, default)
```

返回给定键存储的值，如果没有该键的映射，则返回给定的默认值。

!!! compat "Julia 1.7"
    对于元组和数字，此函数至少需要 Julia 1.7。


# 示例

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> get(d, "a", 3)
1

julia> get(d, "c", 3)
3
```
