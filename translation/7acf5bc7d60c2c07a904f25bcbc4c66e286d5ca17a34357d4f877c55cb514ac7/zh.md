```
config( <see arguments> )
```

仅限关键字的函数，用于配置全局菜单参数

# 参数

  * `charset::Symbol=:na`: 要使用的 UI 字符（`:ascii` 或 `:unicode`）；被其他参数覆盖
  * `cursor::Char='>'|'→'`: 用于光标的字符
  * `up_arrow::Char='^'|'↑'`: 用于上箭头的字符
  * `down_arrow::Char='v'|'↓'`: 用于下箭头的字符
  * `checked::String="[X]"|"✓"`: 用于已选中的字符串
  * `unchecked::String="[ ]"|"⬚")`: 用于未选中的字符串
  * `scroll::Symbol=:nowrap`: 如果 `:wrap` 则在顶部和底部环绕光标，如果 `:nowrap` 则不环绕光标
  * `supress_output::Bool=false`: 被忽略的遗留参数，请将 `suppress_output` 作为关键字参数传递给 `request`。
  * `ctrl_c_interrupt::Bool=true`: 如果为 `false`，在 ^C 时返回空，如果为 `true`，在 ^C 时抛出 InterruptException()

!!! compat "Julia 1.6"
    从 Julia 1.6 开始，`config` 已被弃用。请改用 `Config` 或 `MultiSelectConfig`。

