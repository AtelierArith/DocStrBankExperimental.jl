```
arg_read(f::Function, arg::ArgRead) -> f(arg_io)
```

`arg_read` 函数接受一个参数 `arg`，该参数可以是以下任意一种：

  * `AbstractString`：要打开以进行读取的文件路径
  * `AbstractCmd`：要运行的命令，从其标准输出读取
  * `IO`：要读取的打开的 IO 句柄

无论函数体是正常返回还是抛出错误，打开的路径将在从 `arg_read` 返回之前关闭，而 `IO` 句柄将在从 `arg_read` 返回之前被刷新但不会关闭。

注意：在打开文件时，ArgTools 将向文件 `open(...)` 调用传递 `lock = false`。因此，返回的对象不应在多个线程中使用。此限制在未来可能会放宽，这不会破坏任何正常工作的代码。
