```
unsafe_write(io::IO, ref, nbytes::UInt)
```

将 `ref`（转换为指针）中的 `nbytes` 复制到 `IO` 对象中。

建议子类型 `T<:IO` 重写以下方法签名，以提供更高效的实现：`unsafe_write(s::T, p::Ptr{UInt8}, n::UInt)`
