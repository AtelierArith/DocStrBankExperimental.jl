```
copyuntil(out::IO, stream::IO, delim; keep::Bool = false)
copyuntil(out::IO, filename::AbstractString, delim; keep::Bool = false)
```

从 I/O `stream` 或文件中复制字符串，直到给定的分隔符，将其写入 `out` 流，并返回 `out`。分隔符可以是 `UInt8`、`AbstractChar`、字符串或向量。关键字参数 `keep` 控制分隔符是否包含在结果中。文本假定为 UTF-8 编码。

类似于 [`readuntil`](@ref)，它返回一个 `String`；而 `copyuntil` 直接写入 `out`，而不分配字符串。（这可以用于，例如，将数据读取到预分配的 [`IOBuffer`](@ref) 中。）

# 示例

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", 'L')))
"Julia"

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", '.', keep = true)))
"JuliaLang is a GitHub organization."

julia> rm("my_file.txt")
```
