```
disable_logging(level)
```

禁用所有日志消息，日志级别等于或低于 `level`。这是一个 *全局* 设置，旨在使调试日志在禁用时极其便宜。

# 示例

```julia
Logging.disable_logging(Logging.Info) # 禁用调试和信息
```
