```
count_zeros(x::Integer) -> Integer
```

`x` 的二进制表示中零的数量。

# 示例

```jldoctest
julia> count_zeros(Int32(2 ^ 16 - 1))
16

julia> count_zeros(-1)
0
```
