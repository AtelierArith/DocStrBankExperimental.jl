```
keypress(m::AbstractMenu, i::UInt32) -> Bool
```

处理任何非标准的按键事件。如果返回 `true`，则 [`TerminalMenus.request`](@ref) 将退出。默认为 `false`。
