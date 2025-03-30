```
addenv(command::Cmd, env...; inherit::Bool = true)
```

将新的环境映射合并到给定的 [`Cmd`](@ref) 对象中，返回一个新的 `Cmd` 对象。重复的键会被替换。如果 `command` 中尚未设置任何环境值，则在 `inherit` 为 `true` 时，它会继承 `addenv()` 调用时的当前环境。值为 `nothing` 的键会从环境中删除。

另请参见 [`Cmd`](@ref), [`setenv`](@ref), [`ENV`](@ref).

!!! compat "Julia 1.6"
    此函数需要 Julia 1.6 或更高版本。

