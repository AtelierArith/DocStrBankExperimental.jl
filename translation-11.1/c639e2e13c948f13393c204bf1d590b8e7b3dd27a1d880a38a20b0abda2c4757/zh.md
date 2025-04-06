```
readuntil(stream::IO, delim; keep::Bool = false)
readuntil(filename::AbstractString, delim; keep::Bool = false)
```

从 I/O `stream` 或文件中读取字符串，直到给定的分隔符。分隔符可以是 `UInt8`、`AbstractChar`、字符串或向量。关键字参数 `keep` 控制分隔符是否包含在结果中。文本假定为 UTF-8 编码。

如果 `delim` 是 `AbstractChar` 或字符串，则返回 `String`，否则返回 `Vector{typeof(delim)}`。另请参见 [`copyuntil`](@ref)，以便将内容就地写入另一个流（可以是预分配的 [`IOBuffer`](@ref)）。

# 示例

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readuntil("my_file.txt", 'L')
"Julia"

julia> readuntil("my_file.txt", '.', keep = true)
"JuliaLang is a GitHub organization."

julia> rm("my_file.txt")
```
