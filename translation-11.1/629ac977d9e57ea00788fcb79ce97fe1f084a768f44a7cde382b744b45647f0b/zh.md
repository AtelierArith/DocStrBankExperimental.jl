```
base64decode(string)
```

解码 base64 编码的 `string` 并返回解码字节的 `Vector{UInt8}`。

另见 [`base64encode`](@ref)。

# 示例

```jldoctest
julia> b = base64decode("SGVsbG8h")
6-element Vector{UInt8}:
 0x48
 0x65
 0x6c
 0x6c
 0x6f
 0x21

julia> String(b)
"Hello!"
```
