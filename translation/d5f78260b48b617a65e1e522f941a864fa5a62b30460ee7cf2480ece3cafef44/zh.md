```
start_worker([out::IO=stdout], cookie::AbstractString=readline(stdin); close_stdin::Bool=true, stderr_to_stdout::Bool=true)
```

`start_worker` 是一个内部函数，是通过 TCP/IP 连接的工作进程的默认入口点。它将进程设置为 Julia 集群工作者。

主机:端口 信息被写入流 `out`（默认为 stdout）。

该函数在需要时从 stdin 读取 cookie，并在一个空闲端口上监听（或者如果指定，则在 `--bind-to` 命令行选项中指定的端口上）并调度任务以处理传入的 TCP 连接和请求。它还（可选地）关闭 stdin 并将 stderr 重定向到 stdout。

它不返回。
