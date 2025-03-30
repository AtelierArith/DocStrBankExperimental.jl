```
realloc(addr::Ptr, size::Integer) -> Ptr{Cvoid}
```

从 C 标准库调用 `realloc`。

请参阅 [`free`](@ref) 文档中的警告，仅在最初从 [`malloc`](@ref) 获取的内存上使用此函数。
