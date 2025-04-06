```
fetch(;include_meta = true) -> data
```

返回配置文件回溯的缓冲区副本。请注意，`data` 中的值仅在当前会话的此机器上有意义，因为它依赖于 JIT 编译中使用的确切内存地址。此函数主要供内部使用；对于大多数用户来说，[`retrieve`](@ref) 可能是更好的选择。默认情况下，包括线程 ID 和任务 ID 等元数据。将 `include_meta` 设置为 `false` 以去除元数据。
