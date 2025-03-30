```
无符号 <: 整数
```

所有无符号整数的抽象超类型。

内置的无符号整数以十六进制形式打印，前缀为 `0x`，并且可以以相同的方式输入。

# 示例

```
julia> typemax(UInt8)
0xff

julia> Int(0x00d)
13

julia> unsigned(true)
0x0000000000000001
```
