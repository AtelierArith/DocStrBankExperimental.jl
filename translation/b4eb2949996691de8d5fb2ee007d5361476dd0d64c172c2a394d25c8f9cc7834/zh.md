```
skip(s, offset)
```

相对于当前位置跳过流。

# 示例

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> seek(io, 5);

julia> skip(io, 10);

julia> read(io, Char)
'G': ASCII/Unicode U+0047 (类别 Lu: 字母，大写)
```
