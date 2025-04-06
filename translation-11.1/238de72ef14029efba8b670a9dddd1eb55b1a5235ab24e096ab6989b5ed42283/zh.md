```
mkdir(path::AbstractString; mode::Unsigned = 0o777)
```

创建一个名为 `path` 的新目录，权限为 `mode`。`mode` 默认为 `0o777`，并受到当前文件创建掩码的影响。此函数从不创建超过一个目录。如果目录已经存在，或者某些中间目录不存在，此函数会抛出错误。请参见 [`mkpath`](@ref) 以获取创建所有所需中间目录的函数。返回 `path`。

# 示例

```julia-repl
julia> mkdir("testingdir")
"testingdir"

julia> cd("testingdir")

julia> pwd()
"/home/JuliaUser/testingdir"
```
