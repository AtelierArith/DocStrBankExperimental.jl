```
MultiSelectConfig(; charset=:ascii, checked::String, unchecked::String, kwargs...)
```

通过关键字参数配置多选菜单的行为：

  * `checked` 是选项被选中时打印的字符串。默认值为 "[X]" 或 "✓"，具体取决于 `charset`。
  * `unchecked` 是选项未被选中时打印的字符串。默认值为 "[ ]" 或 "⬚"，具体取决于 `charset`。

所有其他关键字参数的描述请参见 [`TerminalMenus.Config`](@ref)。`checked` 和 `unchecked` 不会自动打印，应该由你的 `writeline` 方法打印。

!!! compat "Julia 1.6"
    `MultiSelectConfig` 从 Julia 1.6 开始可用。在旧版本中使用全局 `CONFIG`。

