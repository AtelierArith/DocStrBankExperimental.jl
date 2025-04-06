```
splitpath(path::AbstractString) -> Vector{String}
```

将文件路径拆分为所有路径组件。这是 `joinpath` 的反操作。返回一个子字符串数组，每个目录或文件在路径中都有一个，包括根目录（如果存在）。

!!! compat "Julia 1.1"
    此函数至少需要 Julia 1.1。


# 示例

```jldoctest
julia> splitpath("/home/myuser/example.jl")
4-element Vector{String}:
 "/"
 "home"
 "myuser"
 "example.jl"
```
