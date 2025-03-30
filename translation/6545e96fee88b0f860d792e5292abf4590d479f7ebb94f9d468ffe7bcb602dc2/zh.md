```
arg_write(f::Function, arg::ArgWrite) -> arg
arg_write(f::Function, arg::Nothing) -> tempname()
```

`arg_read` 函数接受一个参数 `arg`，可以是以下任意类型：

  * `AbstractString`：要打开以进行写入的文件路径
  * `AbstractCmd`：要运行的命令，写入其标准输入
  * `IO`：要写入的打开的 IO 句柄
  * `Nothing`：应写入临时路径

如果主体正常返回，打开的路径将在完成时关闭；IO 句柄参数在返回前保持打开但会被刷新。如果参数是 `nothing`，则会打开一个临时路径进行写入，并在完成时关闭该路径，并从 `arg_write` 返回该路径。在所有其他情况下，返回 `arg` 本身。这是一个有用的模式，因为无论是否传递了参数，您都可以一致地返回所写的内容。

如果在主体的评估过程中发生错误，由 `arg_write` 打开的写入路径将被删除，无论它是作为字符串传递的还是在 `arg` 为 `nothing` 时生成的临时路径。

注意：在打开文件时，ArgTools 将向文件 `open(...)` 调用传递 `lock = false`。因此，从多个线程使用此函数返回的对象是不安全的。未来可能会放宽此限制，这不会破坏任何正常工作的代码。
