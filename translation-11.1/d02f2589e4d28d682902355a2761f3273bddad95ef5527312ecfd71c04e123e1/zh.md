```
@b_str
```

使用字符串语法创建一个不可变的字节（`UInt8`）向量。

# 示例

```jldoctest
julia> v = b"12\x01\x02"
4-element Base.CodeUnits{UInt8, String}:
 0x31
 0x32
 0x01
 0x02

julia> v[2]
0x32
```
