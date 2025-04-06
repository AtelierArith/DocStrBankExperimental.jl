```
unsafe_read(io::IO, ref, nbytes::UInt)
```

将 `nbytes` 从 `IO` 流对象复制到 `ref`（转换为指针）。

建议子类型 `T<:IO` 重写以下方法签名，以提供更高效的实现：`unsafe_read(s::T, p::Ptr{UInt8}, n::UInt)`
