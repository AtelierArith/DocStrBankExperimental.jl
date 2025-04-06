```
count_ones(x::Integer) -> Integer
```

`x` 的二进制表示中 1 的数量。

# 示例

```jldoctest
julia> count_ones(7)
3

julia> count_ones(Int32(-1))
32
```
