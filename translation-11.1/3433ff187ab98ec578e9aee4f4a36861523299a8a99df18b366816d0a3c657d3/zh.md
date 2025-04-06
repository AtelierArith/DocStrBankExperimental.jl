```
put!(rr::RemoteChannel, args...)
```

将一组值存储到 [`RemoteChannel`](@ref)。如果通道已满，则阻塞直到有空间可用。返回第一个参数。
