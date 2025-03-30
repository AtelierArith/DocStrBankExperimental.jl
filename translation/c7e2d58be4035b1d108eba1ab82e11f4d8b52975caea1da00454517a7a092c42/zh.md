```
read(s::IOStream, nb::Integer; all=true)
```

从 `s` 中最多读取 `nb` 字节，返回读取的字节的 `Vector{UInt8}`。

如果 `all` 为 `true`（默认值），此函数将阻塞并反复尝试读取所有请求的字节，直到发生错误或文件结束。如果 `all` 为 `false`，则最多执行一次 `read` 调用，返回的数据量依赖于设备。请注意，并非所有流类型都支持 `all` 选项。
