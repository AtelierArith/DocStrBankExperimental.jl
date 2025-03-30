```
normpath(path::AbstractString, paths::AbstractString...) -> String
```

通过将一组路径连接在一起并删除“.”和“..”条目，将其转换为规范路径。等效于 `normpath(joinpath(path, paths...))`。
