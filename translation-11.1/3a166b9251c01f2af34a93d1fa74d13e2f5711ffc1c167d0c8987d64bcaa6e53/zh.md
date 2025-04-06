```
edit(path::AbstractString, line::Integer=0, column::Integer=0)
```

编辑一个文件或目录，可以选择提供一个行号以在该行编辑文件。退出编辑器时返回到 `julia` 提示符。可以通过设置环境变量 `JULIA_EDITOR`、`VISUAL` 或 `EDITOR` 来更改编辑器。

!!! compat "Julia 1.9"
    `column` 参数至少需要 Julia 1.9。


另见 [`InteractiveUtils.define_editor`](@ref).
