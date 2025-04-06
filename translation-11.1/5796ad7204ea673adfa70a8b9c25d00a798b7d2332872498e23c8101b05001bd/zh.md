```
UInt
```

Sys.WORD_SIZE位无符号整数类型，`UInt <: Unsigned <: Integer`。

像[`Int`](@ref Int)一样，别名`UInt`可能指向`UInt32`或`UInt64`，具体取决于给定计算机上`Sys.WORD_SIZE`的值。

以十六进制打印和解析：`UInt(15) === 0x000000000000000f`。
