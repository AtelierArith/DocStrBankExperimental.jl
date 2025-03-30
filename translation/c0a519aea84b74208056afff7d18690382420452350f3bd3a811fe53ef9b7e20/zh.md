```
Config(; scroll_wrap=false, ctrl_c_interrupt=true, charset=:ascii, cursor::Char, up_arrow::Char, down_arrow::Char)
```

通过关键字参数配置选择菜单的行为：

  * `scroll_wrap`，如果为 `true`，则在滚动超过第一个或低于最后一个条目时，菜单会循环。
  * `ctrl_c_interrupt`，如果为 `true`，则在用户在菜单选择期间按下 Ctrl-C 时抛出 `InterruptException`。如果为 `false`，[`TerminalMenus.request`](@ref) 将返回 [`TerminalMenus.selected`](@ref) 的默认结果。
  * `charset` 影响 `cursor`、`up_arrow` 和 `down_arrow` 的默认值，可以是 `:ascii` 或 `:unicode`。
  * `cursor` 是打印的字符，用于指示将通过按 "Enter" 选择的选项。默认值为 '>' 或 '→'，具体取决于 `charset`。
  * `up_arrow` 是在显示不包括第一个条目时打印的字符。默认值为 '^' 或 '↑'，具体取决于 `charset`。
  * `down_arrow` 是在显示不包括最后一个条目时打印的字符。默认值为 'v' 或 '↓'，具体取决于 `charset`。

`ConfiguredMenu` 的子类型将根据需要自动打印 `cursor`、`up_arrow` 和 `down_arrow`，您的 `writeline` 方法不应打印它们。

!!! compat "Julia 1.6"
    `Config` 从 Julia 1.6 开始可用。在较旧的版本中使用全局 `CONFIG`。

