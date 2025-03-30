```
hex2bytes!(dest::AbstractVector{UInt8}, itr)
```

将表示十六进制字符串的字节可迭代对象 `itr` 转换为其二进制表示，类似于 [`hex2bytes`](@ref)，但输出是就地写入 `dest`。`dest` 的长度必须是 `itr` 长度的一半。

!!! compat "Julia 1.7"
    使用生成 UInt8 的迭代器调用 hex2bytes! 需要版本 1.7。在早期版本中，您可以在调用之前收集可迭代对象。

