```
run(command, args...; wait::Bool = true)
```

运行一个命令对象，该对象使用反引号构造（请参见手册中的 [Running External Programs](@ref) 部分）。如果出现任何问题，包括进程以非零状态退出（当 `wait` 为 true 时），则会抛出错误。

`args...` 允许您将文件描述符传递给命令，并且按常规 unix 文件描述符的顺序排列（例如 `stdin, stdout, stderr, FD(3), FD(4)...`）。

如果 `wait` 为 false，进程将异步运行。您可以稍后等待它并通过在返回的进程对象上调用 `success` 来检查其退出状态。

当 `wait` 为 false 时，进程的 I/O 流被定向到 `devnull`。当 `wait` 为 true 时，I/O 流与父进程共享。使用 [`pipeline`](@ref) 来控制 I/O 重定向。
