```
Base64EncodePipe(ostream)
```

返回一个新的只写I/O流，它将写入其中的任何字节转换为写入`ostream`的base64编码ASCII字节。对`Base64EncodePipe`流调用[`close`](@ref)是完成编码所必需的（但不会关闭`ostream`）。

# 示例

```jldoctest
julia> io = IOBuffer();

julia> iob64_encode = Base64EncodePipe(io);

julia> write(iob64_encode, "Hello!")
6

julia> close(iob64_encode);

julia> str = String(take!(io))
"SGVsbG8h"

julia> String(base64decode(str))
"Hello!"
```
