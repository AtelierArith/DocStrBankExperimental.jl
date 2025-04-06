```
mkpath(path::AbstractString; mode::Unsigned = 0o777)
```

根据需要创建`path`中的所有中间目录。目录的权限为`mode`，默认为`0o777`，并受到当前文件创建掩码的影响。与[`mkdir`](@ref)不同，如果`path`（或其部分）已经存在，`mkpath`不会报错。然而，如果`path`（或其部分）指向一个已存在的文件，则会抛出错误。返回`path`。

如果`path`包含文件名，您可能希望使用`mkpath(dirname(path))`来避免使用文件名创建目录。

# 示例

```julia-repl
julia> cd(mktempdir())

julia> mkpath("my/test/dir") # 创建三个目录
"my/test/dir"

julia> readdir()
1-element Array{String,1}:
 "my"

julia> cd("my")

julia> readdir()
1-element Array{String,1}:
 "test"

julia> readdir("test")
1-element Array{String,1}:
 "dir"

julia> mkpath("intermediate_dir/actually_a_directory.txt") # 创建两个目录
"intermediate_dir/actually_a_directory.txt"

julia> isdir("intermediate_dir/actually_a_directory.txt")
true

```
