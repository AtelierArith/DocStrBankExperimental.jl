```
include_dependency(path::AbstractString; track_content::Bool=true)
```

在一个模块中，声明由 `path` 指定的文件、目录或符号链接（相对或绝对）是预编译的依赖项；也就是说，如果 `track_content=true`，则如果 `path` 的内容发生变化，模块将需要重新编译（如果 `path` 是一个目录，则内容等于 `join(readdir(path))`）。如果 `track_content=false`，则在 `path` 的修改时间 `mtime` 发生变化时触发重新编译。

只有在您的模块依赖于未通过 [`include`](@ref) 使用的路径时，这才是必要的。它在编译之外没有影响。

!!! compat "Julia 1.11"
    关键字参数 `track_content` 至少需要 Julia 1.11。如果 `path` 不可读，则会抛出错误。

