```
pwd() -> String
```

获取当前工作目录。

另见：[`cd`](@ref), [`tempdir`](@ref)。

# 示例

```julia-repl
julia> pwd()
"/home/JuliaUser"

julia> cd("/home/JuliaUser/Projects/julia")

julia> pwd()
"/home/JuliaUser/Projects/julia"
```
