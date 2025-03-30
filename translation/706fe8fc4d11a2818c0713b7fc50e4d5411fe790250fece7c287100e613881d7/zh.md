```
seek(s, pos)
```

将流定位到给定位置。

# 示例

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization.");

julia> seek(io, 5);

julia> read(io, Char)
'L': ASCII/Unicode U+004C (类别 Lu: 字母, 大写)
```
