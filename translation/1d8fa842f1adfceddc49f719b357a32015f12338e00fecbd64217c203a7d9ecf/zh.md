```
Profile.Allocs.print([io::IO = stdout,] [data::AllocResults = fetch()]; kwargs...)
```

将分析结果打印到 `io`（默认情况下为 `stdout`）。如果您不提供 `data` 向量，将使用累积回溯的内部缓冲区。

有关有效关键字参数的解释，请参见 `Profile.print`。
