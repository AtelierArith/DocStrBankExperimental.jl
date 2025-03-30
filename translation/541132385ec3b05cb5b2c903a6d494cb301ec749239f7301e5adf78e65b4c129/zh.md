```
walkdir(dir; topdown=true, follow_symlinks=false, onerror=throw)
```

返回一个迭代器，该迭代器遍历目录的目录树。迭代器返回一个包含 `(rootpath, dirs, files)` 的元组。目录树可以自上而下或自下而上遍历。如果 `walkdir` 或 `stat` 遇到 `IOError`，它将默认重新抛出错误。可以通过 `onerror` 关键字参数提供自定义错误处理函数。`onerror` 以 `IOError` 作为参数调用。

另见: [`readdir`](@ref)。

# 示例

```julia
for (root, dirs, files) in walkdir(".")
    println("Directories in $root")
    for dir in dirs
        println(joinpath(root, dir)) # 目录的路径
    end
    println("Files in $root")
    for file in files
        println(joinpath(root, file)) # 文件的路径
    end
end
```

```julia-repl
julia> mkpath("my/test/dir");

julia> itr = walkdir("my");

julia> (root, dirs, files) = first(itr)
("my", ["test"], String[])

julia> (root, dirs, files) = first(itr)
("my/test", ["dir"], String[])

julia> (root, dirs, files) = first(itr)
("my/test/dir", String[], String[])
```
