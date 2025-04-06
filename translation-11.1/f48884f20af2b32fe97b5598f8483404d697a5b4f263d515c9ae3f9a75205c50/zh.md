```
print([io::IO = stdout,] data::Vector, lidict::LineInfoDict; kwargs...)
```

将剖析结果打印到 `io`。此变体用于检查由先前调用 [`retrieve`](@ref) 导出的结果。提供包含回溯的向量 `data` 和包含行信息的字典 `lidict`。

有关有效关键字参数的说明，请参见 `Profile.print([io], data)`。
