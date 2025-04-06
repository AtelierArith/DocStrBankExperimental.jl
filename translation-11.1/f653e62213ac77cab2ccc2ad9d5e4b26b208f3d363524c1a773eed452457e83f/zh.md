```
Char(c::Union{Number,AbstractChar})
```

`Char` 是一个 32 位的 [`AbstractChar`](@ref) 类型，是 Julia 中字符的默认表示。`Char` 是用于字符字面量的类型，如 `'x'`，它也是 [`String`](@ref) 的元素类型。

为了无损地表示存储在 `String` 中的任意字节流，`Char` 值可能存储无法转换为 Unicode 代码点的信息 — 将这样的 `Char` 转换为 `UInt32` 将抛出错误。可以使用 [`isvalid(c::Char)`](@ref) 函数查询 `c` 是否表示有效的 Unicode 字符。
