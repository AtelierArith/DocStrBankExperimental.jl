```
bytesavailable(io)
```

返回在从此流或缓冲区读取之前可供读取的字节数，否则将会阻塞。

# 示例

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> bytesavailable(io)
34
```
