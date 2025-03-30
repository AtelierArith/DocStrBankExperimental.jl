```
isreadonly(io) -> Bool
```

确定一个流是否为只读。

# 示例

```jldoctest
julia> io = IOBuffer("JuliaLang is a GitHub organization");

julia> isreadonly(io)
true

julia> io = IOBuffer();

julia> isreadonly(io)
false
```
