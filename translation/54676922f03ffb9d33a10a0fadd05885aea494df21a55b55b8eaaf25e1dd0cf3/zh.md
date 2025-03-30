```
ConsoleLogger([stream,] min_level=Info; meta_formatter=default_metafmt,
              show_limited=true, right_justify=0)
```

具有优化可读性的格式的记录器，适用于文本控制台，例如与 Julia REPL 的交互式工作。

低于 `min_level` 的日志级别将被过滤掉。

消息格式可以通过设置关键字参数来控制：

  * `meta_formatter` 是一个函数，它接受日志事件元数据 `(level, _module, group, id, file, line)` 并返回一个颜色（如同传递给 printstyled 的那样）、日志消息的前缀和后缀。默认情况下，前缀为日志级别，后缀包含模块、文件和行位置。
  * `show_limited` 通过在格式化期间设置 `:limit` `IOContext` 键，限制大型数据结构的打印，以适应屏幕。
  * `right_justify` 是日志元数据右对齐的整数列。默认值为零（元数据单独占一行）。
