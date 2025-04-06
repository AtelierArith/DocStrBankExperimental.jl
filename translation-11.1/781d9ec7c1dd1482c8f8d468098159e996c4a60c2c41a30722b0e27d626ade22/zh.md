```
IOBuffer(string::String)
```

在给定字符串的基础上创建一个只读的 `IOBuffer`。

# 示例

```jldoctest
julia> io = IOBuffer("Haho");

julia> String(take!(io))
"Haho"

julia> String(take!(io))
"Haho"
```
