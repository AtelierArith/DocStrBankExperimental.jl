```
codepoint(c::AbstractChar) -> Integer
```

返回与字符 `c` 对应的 Unicode 代码点（一个无符号整数）（如果 `c` 不代表有效字符，则抛出异常）。对于 `Char`，这是一个 `UInt32` 值，但仅表示 Unicode 子集的 `AbstractChar` 类型可能返回不同大小的整数（例如 `UInt8`）。
