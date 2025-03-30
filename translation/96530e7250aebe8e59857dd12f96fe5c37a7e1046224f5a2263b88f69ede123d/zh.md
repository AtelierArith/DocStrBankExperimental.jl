```
crc32c(data, crc::UInt32=0x00000000)
```

计算给定 `data` 的 CRC-32c 校验和，`data` 可以是 `Array{UInt8}`、其连续子数组或 `String`。可选地，您可以传递一个起始的 `crc` 整数与校验和混合。`crc` 参数可用于计算分块数据的校验和：执行 `crc32c(data2, crc32c(data1))` 相当于 `[data1; data2]` 的校验和。（从技术上讲，计算的是小端校验和。）

还有一个方法 `crc32c(io, nb, crc)` 用于从流 `io` 中校验 `nb` 字节，或 `crc32c(io, crc)` 用于校验所有剩余字节。因此，您可以执行 [`open(crc32c, filename)`](@ref) 来校验整个文件，或 `crc32c(seekstart(buf))` 来校验一个 [`IOBuffer`](@ref) 而不调用 [`take!`](@ref)。

对于 `String`，请注意结果特定于 UTF-8 编码（不同的 Unicode 编码会得到不同的校验和）。要对某种其他位类型的 `a::Array` 进行校验，您可以执行 `crc32c(reinterpret(UInt8,a))`，但请注意结果可能依赖于字节序。
