```
open(command, stdio=devnull; write::Bool = false, read::Bool = !write)
```

开始异步运行 `command`，并返回一个 `process::IO` 对象。如果 `read` 为真，则从进程的标准输出读取数据，`stdio` 可选地指定进程的标准输入流。如果 `write` 为真，则写入数据到进程的标准输入，`stdio` 可选地指定进程的标准输出流。进程的标准错误流连接到当前全局的 `stderr`。
