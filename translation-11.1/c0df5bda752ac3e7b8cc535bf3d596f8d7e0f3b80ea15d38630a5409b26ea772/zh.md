```
rm(path::AbstractString; force::Bool=false, recursive::Bool=false)
```

删除给定路径下的文件、链接或空目录。如果传递了 `force=true`，则不存在的路径不会被视为错误。如果传递了 `recursive=true` 并且路径是一个目录，则所有内容将被递归删除。

# 示例

```jldoctest
julia> mkpath("my/test/dir");

julia> rm("my", recursive=true)

julia> rm("this_file_does_not_exist", force=true)

julia> rm("this_file_does_not_exist")
ERROR: IOError: unlink("this_file_does_not_exist"): no such file or directory (ENOENT)
Stacktrace:
[...]
```
