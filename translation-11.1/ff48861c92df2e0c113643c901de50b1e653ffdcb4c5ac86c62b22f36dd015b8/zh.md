```
istextmime(m::MIME)
```

确定一个 MIME 类型是否为文本数据。MIME 类型被假定为二进制数据，除非是已知为文本数据（可能是 Unicode）的一组类型。

# 示例

```jldoctest
julia> istextmime(MIME("text/plain"))
true

julia> istextmime(MIME("image/png"))
false
```
