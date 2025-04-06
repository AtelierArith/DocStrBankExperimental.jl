```
open(filename::AbstractString, [mode::AbstractString]; lock = true) -> IOStream
```

打开的替代语法，其中使用基于字符串的模式说明符，而不是五个布尔值。`mode` 的值对应于 `fopen(3)` 或 Perl `open` 中的值，并等同于设置以下布尔组：

| 模式   | 描述          | 关键字                            |
|:---- |:----------- |:------------------------------ |
| `r`  | 读取          | 无                              |
| `w`  | 写入，创建，截断    | `write = true`                 |
| `a`  | 写入，创建，追加    | `append = true`                |
| `r+` | 读取，写入       | `read = true, write = true`    |
| `w+` | 读取，写入，创建，截断 | `truncate = true, read = true` |
| `a+` | 读取，写入，创建，追加 | `append = true, read = true`   |

`lock` 关键字参数控制操作是否会被锁定以确保安全的多线程访问。

# 示例

```jldoctest
julia> io = open("myfile.txt", "w");

julia> write(io, "Hello world!");

julia> close(io);

julia> io = open("myfile.txt", "r");

julia> read(io, String)
"Hello world!"

julia> write(io, "This file is read only")
ERROR: ArgumentError: write failed, IOStream is not writeable
[...]

julia> close(io)

julia> io = open("myfile.txt", "a");

julia> write(io, "This stream is not read only")
28

julia> close(io)

julia> rm("myfile.txt")
```

!!! compat "Julia 1.5"
    `lock` 参数自 Julia 1.5 起可用。

