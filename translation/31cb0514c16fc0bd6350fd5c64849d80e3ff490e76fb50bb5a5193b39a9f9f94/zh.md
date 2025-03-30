```
leading_ones(x::Integer) -> Integer
```

`x` 的二进制表示中前导的 1 的数量。

# 示例

```jldoctest
julia> leading_ones(UInt32(2 ^ 32 - 2))
31
```
