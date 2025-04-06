```
digits!(array, n::Integer; base::Integer = 10)
```

填充一个数组，包含在给定进制下 `n` 的数字。更高位的数字位于更高的索引。如果数组长度不足，则填充最不重要的数字直到数组长度。如果数组长度过长，则多余的部分用零填充。

# 示例

```jldoctest
julia> digits!([2, 2, 2, 2], 10, base = 2)
4-element Vector{Int64}:
 0
 1
 0
 1

julia> digits!([2, 2, 2, 2, 2, 2], 10, base = 2)
6-element Vector{Int64}:
 0
 1
 0
 1
 0
 0
```
