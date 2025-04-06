```
bytes2hex(itr) -> String
bytes2hex(io::IO, itr)
```

将字节迭代器 `itr` 转换为其十六进制字符串表示，可以通过 `bytes2hex(itr)` 返回一个 `String`，或者通过 `bytes2hex(io, itr)` 将字符串写入 `io` 流。十六进制字符均为小写。

!!! compat "Julia 1.7"
    使用生成 `UInt8` 值的任意迭代器调用 `bytes2hex` 需要 Julia 1.7 或更高版本。在早期版本中，您可以在调用 `bytes2hex` 之前 `collect` 迭代器。


# 示例

```jldoctest
julia> a = string(12345, base = 16)
"3039"

julia> b = hex2bytes(a)
2-element Vector{UInt8}:
 0x30
 0x39

julia> bytes2hex(b)
"3039"
```
