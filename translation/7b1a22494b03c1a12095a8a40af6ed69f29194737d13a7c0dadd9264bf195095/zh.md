```
LogLevel(level)
```

日志记录的严重性/详细程度。

日志级别提供了一个关键字，可以在构建日志记录数据结构之前，对潜在的日志记录进行过滤。

# 示例

```julia-repl
julia> Logging.LogLevel(0) == Logging.Info
true
```
