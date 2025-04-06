```
writeline(buf::IO, m::AbstractMenu, idx::Int, iscursor::Bool)
```

将索引为 `idx` 的选项写入 `buf`。如果 `iscursor` 为 `true`，则表示该项位于当前光标位置（即按下 "Enter" 时将被选中的项）。

如果 `m` 是 `ConfiguredMenu`，`TerminalMenus` 将打印光标指示器。否则，调用者需要处理此类打印。

!!! compat "Julia 1.6"
    `writeline` 需要 Julia 1.6 或更高版本。

    在旧版本的 Julia 中，这个函数是 `writeLine(buf::IO, m::AbstractMenu, idx, iscursor::Bool)`，并且假定 `m` 是未配置的。选择和光标指示器可以从 `TerminalMenus.CONFIG` 中获取。

    这个旧函数在所有 Julia 1.x 版本中都受支持，但将在 Julia 2.0 中被删除。

