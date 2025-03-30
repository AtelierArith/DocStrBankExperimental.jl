```
Base64DecodePipe(istream)
```

返回一个新的只读I/O流，该流解码从`istream`读取的base64编码数据。

# 示例

```jldoctest
julia> io = IOBuffer();

julia> iob64_decode = Base64DecodePipe(io);

julia> write(io, "SGVsbG8h")
8

julia> seekstart(io);

julia> String(read(iob64_decode))
"Hello!"
```
