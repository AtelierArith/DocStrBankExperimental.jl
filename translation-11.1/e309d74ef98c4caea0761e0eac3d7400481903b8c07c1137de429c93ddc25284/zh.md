```
take!(b::IOBuffer)
```

获取 `IOBuffer` 的内容作为数组。之后，`IOBuffer` 被重置为其初始状态。

# 示例

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."
```
