```
evalfile(path::AbstractString, args::Vector{String}=String[])
```

将文件加载到一个匿名模块中，使用 [`include`](@ref)，评估所有表达式，并返回最后一个表达式的值。可选的 `args` 参数可用于设置脚本的输入参数（即全局 `ARGS` 变量）。请注意，定义（例如方法、全局变量）在匿名模块中被评估，不会影响当前模块。

# 示例

```jldoctest
julia> write("testfile.jl", """
           @show ARGS
           1 + 1
       """);

julia> x = evalfile("testfile.jl", ["ARG1", "ARG2"]);
ARGS = ["ARG1", "ARG2"]

julia> x
2

julia> rm("testfile.jl")
```
