```
errormonitor(t::Task)
```

如果任务 `t` 失败，则将错误日志打印到 `stderr`。

# 示例

```julia-repl
julia> Base._wait(errormonitor(Threads.@spawn error("任务失败")))
未处理的任务错误：任务失败
堆栈跟踪：
[...]
```
