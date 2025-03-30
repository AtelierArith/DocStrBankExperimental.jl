```
dirname(path::AbstractString) -> String
```

获取路径的目录部分。路径中的尾随字符（'/' 或 '\'）被视为路径的一部分。

# 示例

```jldoctest
julia> dirname("/home/myuser")
"/home"

julia> dirname("/home/myuser/")
"/home/myuser"
```

另见 [`basename`](@ref).
