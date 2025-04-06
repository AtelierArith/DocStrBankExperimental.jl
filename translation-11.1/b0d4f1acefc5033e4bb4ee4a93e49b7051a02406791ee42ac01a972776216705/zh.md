```
copyline(out::IO, io::IO=stdin; keep::Bool=false)
copyline(out::IO, filename::AbstractString; keep::Bool=false)
```

从 I/O `流` 或文件中复制一行文本到 `out` 流，返回 `out`。

当从文件中读取时，文本假定为 UTF-8 编码。输入中的行以 `'\n'` 或 `"\r\n"` 或输入流的结束符结束。当 `keep` 为 false（默认情况下为 false）时，这些尾随换行符在返回之前会从行中移除。当 `keep` 为 true 时，它们作为行的一部分返回。

类似于 [`readline`](@ref)，它返回一个 `String`；而 `copyline` 直接写入 `out`，而不分配字符串。（这可以用于，例如，将数据读取到预分配的 [`IOBuffer`](@ref) 中。）

另请参见 [`copyuntil`](@ref)，用于读取直到更一般的分隔符。

# 示例

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> String(take!(copyline(IOBuffer(), "my_file.txt")))
"JuliaLang is a GitHub organization."

julia> String(take!(copyline(IOBuffer(), "my_file.txt", keep=true)))
"JuliaLang is a GitHub organization.\n"

julia> rm("my_file.txt")
```
