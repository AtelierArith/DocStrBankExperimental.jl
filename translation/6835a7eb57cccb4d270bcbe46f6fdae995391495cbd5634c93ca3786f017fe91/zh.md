```
link_pipe!(pipe; reader_supports_async=false, writer_supports_async=false)
```

初始化 `pipe` 并将 `in` 端点链接到 `out` 端点。关键字参数 `reader_supports_async`/`writer_supports_async` 对应于 Windows 上的 `OVERLAPPED` 和 POSIX 系统上的 `O_NONBLOCK`。除非将被外部程序使用（例如，通过 [`run`](@ref) 执行的命令的输出），否则它们应该为 `true`。
