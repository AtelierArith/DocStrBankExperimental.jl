```
hex2bytes(itr)
```

给定一个可迭代的 `itr`，其中包含一系列十六进制数字的 ASCII 码，返回一个 `Vector{UInt8}` 的字节，对应于二进制表示：`itr` 中每对连续的十六进制数字给出返回向量中一个字节的值。

`itr` 的长度必须是偶数，返回的数组长度是 `itr` 的一半。另请参见 [`hex2bytes!`](@ref) 的就地版本，以及 [`bytes2hex`](@ref) 的逆操作。

!!! compat "Julia 1.7"
    使用生成 `UInt8` 值的迭代器调用 `hex2bytes` 需要 Julia 1.7 或更高版本。在早期版本中，您可以在调用 `hex2bytes` 之前 `collect` 迭代器。


# 示例

```jldoctest
julia> s = string(12345, base = 16)
"3039"

julia> hex2bytes(s)
2-element Vector{UInt8}:
 0x30
 0x39

julia> a = b"01abEF"
6-element Base.CodeUnits{UInt8, String}:
 0x30
 0x31
 0x61
 0x62
 0x45
 0x46

julia> hex2bytes(a)
3-element Vector{UInt8}:
 0x01
 0xab
 0xef
```
