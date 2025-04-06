```
readbytes!(stream::IOStream, b::AbstractVector{UInt8}, nb=length(b); all::Bool=true)
```

从 `stream` 中最多读取 `nb` 字节到 `b`，返回读取的字节数。如果需要，`b` 的大小将会增加（即如果 `nb` 大于 `length(b)` 并且可以读取足够的字节），但永远不会减少。

如果 `all` 为 `true`（默认值），此函数将会阻塞并重复尝试读取所有请求的字节，直到发生错误或文件结束。如果 `all` 为 `false`，最多只执行一次 `read` 调用，返回的数据量依赖于设备。请注意，并非所有流类型都支持 `all` 选项。
