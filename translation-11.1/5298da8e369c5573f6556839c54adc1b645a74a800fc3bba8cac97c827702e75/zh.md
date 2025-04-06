```
open(f::Function, command, args...; kwargs...)
```

类似于 `open(command, args...; kwargs...)`，但在结果进程流上调用 `f(stream)`，然后关闭输入流并等待进程完成。成功时返回 `f` 返回的值。如果进程失败，或者进程尝试向 stdout 打印任何内容，则抛出错误。
