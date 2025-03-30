```
basename(path::AbstractString) -> String
```

获取路径的文件名部分。

!!! note
    此函数与 Unix 的 `basename` 程序略有不同，后缀斜杠会被忽略，即 `$ basename /foo/bar/` 返回 `bar`，而 Julia 中的 `basename` 返回空字符串 `""`。


# 示例

```jldoctest
julia> basename("/home/myuser/example.jl")
"example.jl"

julia> basename("/home/myuser/")
""
```

另见 [`dirname`](@ref).
