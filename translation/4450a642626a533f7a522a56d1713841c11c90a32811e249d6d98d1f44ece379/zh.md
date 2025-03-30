```
read(s::IO, nb=typemax(Int))
```

从 `s` 中最多读取 `nb` 字节，返回读取的字节的 `Vector{UInt8}`。
