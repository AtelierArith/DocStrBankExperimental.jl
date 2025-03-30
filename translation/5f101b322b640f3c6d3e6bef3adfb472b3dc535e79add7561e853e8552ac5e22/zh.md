```
eachline(io::IO=stdin; keep::Bool=false)
eachline(filename::AbstractString; keep::Bool=false)
```

创建一个可迭代的 `EachLine` 对象，该对象将从 I/O 流或文件中逐行输出。迭代调用 [`readline`](@ref) 在流参数上重复执行，并传递 `keep`，以确定是否保留尾随的行结束符。当使用文件名调用时，文件在迭代开始时打开，并在结束时关闭。如果迭代被中断，文件将在 `EachLine` 对象被垃圾回收时关闭。

要迭代 `String` 的每一行，可以使用 `eachline(IOBuffer(str))`。

可以在 `EachLine` 对象上使用 [`Iterators.reverse`](@ref) 以反向顺序读取行（对于支持 [`seek`](@ref) 的文件、缓冲区和其他 I/O 流），并且可以使用 [`first`](@ref) 或 [`last`](@ref) 分别提取初始或最终行。

# 示例

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\n It has many members.\n");

julia> for line in eachline("my_file.txt")
           print(line)
       end
JuliaLang is a GitHub organization. It has many members.

julia> rm("my_file.txt");
```

!!! compat "Julia 1.8"
    使用 `eachline` 迭代器需要 Julia 1.8 以支持 `Iterators.reverse` 或 `last`。

