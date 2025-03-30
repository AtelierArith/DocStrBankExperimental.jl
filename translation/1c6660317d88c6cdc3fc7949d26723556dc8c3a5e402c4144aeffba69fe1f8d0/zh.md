```
mktempdir(parent=tempdir(); prefix="jl_", cleanup=true) -> path
```

在给定的 `parent` 目录中创建一个临时目录，其名称由给定的 `prefix` 和一个随机后缀构成，并返回其路径。此外，在某些平台上，`prefix` 中的任何尾随 `'X'` 字符可能会被随机字符替换。如果 `parent` 不存在，则抛出错误。`cleanup` 选项控制在进程退出时临时目录是否会被自动删除。

!!! compat "Julia 1.2"
    `prefix` 关键字参数是在 Julia 1.2 中添加的。


!!! compat "Julia 1.3"
    `cleanup` 关键字参数是在 Julia 1.3 中添加的。相关地，从 1.3 开始，Julia 会在 Julia 进程退出时删除由 `mktempdir` 创建的临时路径，除非 `cleanup` 被显式设置为 `false`。


另见: [`mktemp`](@ref), [`mkdir`](@ref).
