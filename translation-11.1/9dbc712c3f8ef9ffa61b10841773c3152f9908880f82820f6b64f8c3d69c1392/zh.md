```
hvcat(blocks_per_row::Union{Tuple{Vararg{Int}}, Int}, values...)
```

在一次调用中进行水平和垂直连接。此函数用于块矩阵语法。第一个参数指定每个块行中要连接的参数数量。如果第一个参数是一个单一整数 `n`，则假定所有块行都有 `n` 个块列。

# 示例

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c; d e f]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> hvcat((3,3), a,b,c,d,e,f)
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> [a b; c d; e f]
3×2 Matrix{Int64}:
 1  2
 3  4
 5  6

julia> hvcat((2,2,2), a,b,c,d,e,f)
3×2 Matrix{Int64}:
 1  2
 3  4
 5  6
julia> hvcat((2,2,2), a,b,c,d,e,f) == hvcat(2, a,b,c,d,e,f)
true
```
