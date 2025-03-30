```
countlines(io::IO; eol::AbstractChar = '\n')
countlines(filename::AbstractString; eol::AbstractChar = '\n')
```

读取 `io` 直到流/文件的末尾并计算行数。要指定文件，请将文件名作为第一个参数传递。通过将其他 EOL 标记作为第二个参数传递来支持。即使最后一行非空的 `io` 不以 EOL 结尾，也会被计入行数，这与 [`eachline`](@ref) 和 [`readlines`](@ref) 返回的长度相匹配。

要计算 `String` 的行数，可以使用 `countlines(IOBuffer(str))`。

# 示例

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.\n");

julia> countlines(io)
1

julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> countlines(io)
1

julia> eof(io) # 计数行会移动文件指针
true

julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> countlines(io, eol = '.')
1
```

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\n")
36

julia> countlines("my_file.txt")
1

julia> countlines("my_file.txt", eol = 'n')
4

julia> rm("my_file.txt")

```
