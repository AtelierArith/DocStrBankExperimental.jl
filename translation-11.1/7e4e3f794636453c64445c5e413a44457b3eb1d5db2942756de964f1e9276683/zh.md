```
IOBuffer([data::AbstractVector{UInt8}]; keywords...) -> IOBuffer
```

创建一个内存中的 I/O 流，可以选择性地操作一个预先存在的数组。

它可以接受可选的关键字参数：

  * `read`, `write`, `append`: 限制操作在缓冲区内；有关详细信息，请参见 `open`。
  * `truncate`: 将缓冲区大小截断为零长度。
  * `maxsize`: 指定缓冲区不能超过的大小。
  * `sizehint`: 建议缓冲区的容量（`data` 必须实现 `sizehint!(data, size)`）。

当未给定 `data` 时，缓冲区默认是可读和可写的。

# 示例

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."

julia> io = IOBuffer(b"JuliaLang is a GitHub organization.")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=35, maxsize=Inf, ptr=1, mark=-1)

julia> read(io, String)
"JuliaLang is a GitHub organization."

julia> write(io, "This isn't writable.")
ERROR: ArgumentError: ensureroom failed, IOBuffer is not writeable

julia> io = IOBuffer(UInt8[], read=true, write=true, maxsize=34)
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=34, ptr=1, mark=-1)

julia> write(io, "JuliaLang is a GitHub organization.")
34

julia> String(take!(io))
"JuliaLang is a GitHub organization"

julia> length(read(IOBuffer(b"data", read=true, truncate=false)))
4

julia> length(read(IOBuffer(b"data", read=true, truncate=true)))
0
```
