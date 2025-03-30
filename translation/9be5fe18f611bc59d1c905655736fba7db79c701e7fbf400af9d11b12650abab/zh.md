```
crc32c(io::IO, [nb::Integer,] crc::UInt32=0x00000000)
```

从 `io` 中读取最多 `nb` 字节并返回 CRC-32c 校验和，可选地与起始的 `crc` 整数混合。如果未提供 `nb`，则将读取 `io` 直到流的末尾。
