```
touch(path::AbstractString)
touch(fd::File)
```

将文件的最后修改时间戳更新为当前时间。

如果文件不存在，则会创建一个新文件。

返回 `path`。

# 示例

```julia-repl
julia> write("my_little_file", 2);

julia> mtime("my_little_file")
1.5273815391135583e9

julia> touch("my_little_file");

julia> mtime("my_little_file")
1.527381559163435e9
```

我们可以看到 [`mtime`](@ref) 已被 `touch` 修改。
