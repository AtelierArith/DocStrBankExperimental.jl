```
init(; n::Integer, delay::Real)
```

配置回溯之间的 `delay`（以秒为单位）和每个线程可以存储的指令指针数量 `n`。每个指令指针对应于一行代码；回溯通常由一长串指令指针组成。请注意，每个回溯使用 6 个空格来存储元数据和两个 NULL 结束标记。可以通过调用此函数而不带参数来获取当前设置，并且可以使用关键字或按顺序 `(n, delay)` 独立设置每个参数。
