```
readbytes!(stream::IO, b::AbstractVector{UInt8}, nb=length(b))
```

从 `stream` 中最多读取 `nb` 个字节到 `b`，返回读取的字节数。如果需要，`b` 的大小将会增加（即如果 `nb` 大于 `length(b)` 并且可以读取足够的字节），但永远不会减少。
