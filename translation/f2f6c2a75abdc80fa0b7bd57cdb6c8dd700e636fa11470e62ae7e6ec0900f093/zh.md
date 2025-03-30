```
callers(funcname, [data, lidict], [filename=<filename>], [linerange=<start:stop>]) -> Vector{Tuple{count, lineinfo}}
```

根据之前的性能分析运行，确定谁调用了特定的函数。提供文件名（可选地，提供函数定义的行号范围）可以帮助你区分重载的方法。返回值是一个向量，包含调用次数和关于调用者的行信息。可以选择性地提供从 [`retrieve`](@ref) 获得的回溯 `data`；否则，将使用当前的内部性能分析缓冲区。
