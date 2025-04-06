```
isvalid(value) -> Bool
```

如果给定的值对于其类型有效，则返回 `true`，目前可以是 `AbstractChar` 或 `String` 或 `SubString{String}`。

# 示例

```jldoctest
julia> isvalid(Char(0xd800))
false

julia> isvalid(SubString(String(UInt8[0xfe,0x80,0x80,0x80,0x80,0x80]),1,2))
false

julia> isvalid(Char(0xd799))
true
```
