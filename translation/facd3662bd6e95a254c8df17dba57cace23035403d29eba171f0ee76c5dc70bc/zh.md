```
SimpleLogger([stream,] min_level=Info)
```

简单的日志记录器，用于将所有级别大于或等于 `min_level` 的消息记录到 `stream`。如果流被关闭，则级别大于或等于 `Warn` 的消息将记录到 `stderr`，而级别较低的消息将记录到 `stdout`。
