```
FILE(::Ptr)
FILE(::IO)
```

一个 libc `FILE*`，表示一个已打开的文件。

它可以作为 `Ptr{FILE}` 参数传递给 [`ccall`](@ref)，并且支持 [`seek`](@ref)、[`position`](@ref) 和 [`close`](@ref)。

可以从普通的 `IO` 对象构造一个 `FILE`，前提是它是一个已打开的文件。之后必须关闭它。

# 示例

```jldoctest
julia> using Base.Libc

julia> mktemp() do _, io
           # 使用 libc 中的 `puts(char*, FILE*)` 写入临时文件
           file = FILE(io)
           ccall(:fputs, Cint, (Cstring, Ptr{FILE}), "hello world", file)
           close(file)
           # 再次读取文件
           seek(io, 0)
           read(io, String)
       end
"hello world"
```
