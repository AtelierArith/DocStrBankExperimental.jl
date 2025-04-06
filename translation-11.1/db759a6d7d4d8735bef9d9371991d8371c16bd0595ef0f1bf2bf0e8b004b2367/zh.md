```
hardlink(src::AbstractString, dst::AbstractString)
```

创建一个指向现有源文件 `src` 的硬链接，名称为 `dst`。目标 `dst` 不能存在。

另见：[`symlink`](@ref)。

!!! compat "Julia 1.8"
    此方法是在 Julia 1.8 中添加的。

