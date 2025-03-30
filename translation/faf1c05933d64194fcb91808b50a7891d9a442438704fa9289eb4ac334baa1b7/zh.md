```
readline(io::IO=stdin; keep::Bool=false)
readline(filename::AbstractString; keep::Bool=false)
```

从给定的 I/O 流或文件中读取一行文本（默认为 `stdin`）。从文件读取时，假定文本编码为 UTF-8。输入中的行以 `'\n'` 或 `"\r\n"` 或输入流的结束结束。当 `keep` 为 false（默认情况下为 false）时，这些尾随换行符在返回之前会从行中删除。当 `keep` 为 true 时，它们作为行的一部分返回。

返回一个 `String`。另请参见 [`copyline`](@ref)，以便在另一个流中就地写入（该流可以是预分配的 [`IOBuffer`](@ref)）。

另请参见 [`readuntil`](@ref)，以便读取直到更一般的分隔符。

# 示例

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readline("my_file.txt")
"JuliaLang is a GitHub organization."

julia> readline("my_file.txt", keep=true)
"JuliaLang is a GitHub organization.\n"

julia> rm("my_file.txt")
```

```julia-repl
julia> print("Enter your name: ")
Enter your name:

julia> your_name = readline()
Logan
"Logan"
```
