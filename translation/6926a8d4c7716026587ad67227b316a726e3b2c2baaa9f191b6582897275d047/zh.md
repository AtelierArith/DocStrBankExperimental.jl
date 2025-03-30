```
clear_malloc_data()
```

在使用 `--track-allocation` 运行 julia 时，清除任何存储的内存分配数据。执行您想要测试的命令（以强制 JIT 编译），然后调用 [`clear_malloc_data`](@ref)。然后再次执行您的命令，退出 Julia，并检查生成的 `*.mem` 文件。
