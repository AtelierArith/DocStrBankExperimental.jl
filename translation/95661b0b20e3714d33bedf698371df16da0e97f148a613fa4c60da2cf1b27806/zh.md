```
readchomp(x)
```

将 `x` 的全部内容作为字符串读取，并在有的情况下去除一个尾随换行符。等价于 `chomp(read(x, String))`。

# 示例

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readchomp("my_file.txt")
"JuliaLang is a GitHub organization.\nIt has many members."

julia> rm("my_file.txt");
```
