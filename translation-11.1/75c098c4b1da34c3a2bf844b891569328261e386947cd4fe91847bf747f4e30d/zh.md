```
normpath(path::AbstractString) -> String
```

规范化路径，移除 "." 和 ".." 条目，并将 "/" 更改为系统的标准路径分隔符。

# 示例

```jldoctest
julia> normpath("/home/myuser/../example.jl")
"/home/example.jl"

julia> normpath("Documents/Julia") == joinpath("Documents", "Julia")
true
```
