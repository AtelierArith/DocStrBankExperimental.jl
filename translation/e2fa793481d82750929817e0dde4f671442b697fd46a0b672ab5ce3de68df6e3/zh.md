```
isascii(cu::AbstractVector{CU}) where {CU <: Integer} -> Bool
```

测试向量中的所有值是否属于 ASCII 字符集（0x00 到 0x7f）。此函数旨在被其他需要快速 ASCII 检查的字符串实现使用。
