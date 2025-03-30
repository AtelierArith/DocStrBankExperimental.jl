```
read(filename::AbstractString)
```

将文件的全部内容读取为 `Vector{UInt8}`。

```
read(filename::AbstractString, String)
```

将文件的全部内容读取为字符串。

```
read(filename::AbstractString, args...)
```

打开一个文件并读取其内容。`args` 被传递给 `read`：这相当于 `open(io->read(io, args...), filename)`。
