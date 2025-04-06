```
open(f::Function, args...; kwargs...)
```

将函数 `f` 应用到 `open(args...; kwargs...)` 的结果上，并在完成后关闭结果文件描述符。

# 示例

```jldoctest
julia> write("myfile.txt", "Hello world!");

julia> open(io->read(io, String), "myfile.txt")
"Hello world!"

julia> rm("myfile.txt")
```
