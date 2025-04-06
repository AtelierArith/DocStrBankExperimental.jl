```
join([io::IO,] iterator [, delim [, last]])
```

将任何 `iterator` 连接成一个单一的字符串，在相邻项之间插入给定的分隔符（如果有的话）。如果给定了 `last`，它将用于最后两个项之间，而不是 `delim`。`iterator` 的每个项通过 `print(io::IOBuffer, x)` 转换为字符串。如果给定了 `io`，结果将写入 `io` 而不是作为 `String` 返回。

# 示例

```jldoctest
julia> join(["apples", "bananas", "pineapples"], ", ", " and ")
"apples, bananas and pineapples"

julia> join([1,2,3,4,5])
"12345"
```
