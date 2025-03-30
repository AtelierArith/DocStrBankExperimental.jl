```
readlines(io::IO=stdin; keep::Bool=false)
readlines(filename::AbstractString; keep::Bool=false)
```

将 I/O 流或文件的所有行作为字符串向量读取。行为等同于使用相同参数重复调用 [`readline`](@ref) 并将结果行保存为字符串向量。另请参见 [`eachline`](@ref)，以便在不一次性读取所有行的情况下迭代行。

# 示例

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readlines("my_file.txt")
2-element Vector{String}:
 "JuliaLang is a GitHub organization."
 "It has many members."

julia> readlines("my_file.txt", keep=true)
2-element Vector{String}:
 "JuliaLang is a GitHub organization.\n"
 "It has many members.\n"

julia> rm("my_file.txt")
```
