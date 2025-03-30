```
abspath(path::AbstractString, paths::AbstractString...) -> String
```

通过将一组路径连接在一起并在必要时添加当前目录，将其转换为绝对路径。等价于 `abspath(joinpath(path, paths...))`。
