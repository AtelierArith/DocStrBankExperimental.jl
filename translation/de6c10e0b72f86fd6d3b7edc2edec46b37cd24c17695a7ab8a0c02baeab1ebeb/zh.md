```
write(io::IO, x)
```

将值的规范二进制表示写入给定的 I/O 流或文件。返回写入流中的字节数。另请参见 [`print`](@ref) 以写入文本表示（其编码可能依赖于 `io`）。

写入值的字节序取决于主机系统的字节序。在写入/读取时转换为/从固定字节序（例如使用 [`htol`](@ref) 和 [`ltoh`](@ref)）以获得跨平台一致的结果。

您可以使用相同的 `write` 调用写入多个值。即以下两者是等效的：

```
write(io, x, y...)
write(io, x) + write(io, y...)
```

# 示例

一致的序列化：

```jldoctest
julia> fname = tempname(); # 随机临时文件名

julia> open(fname,"w") do f
           # 确保我们以小端字节顺序写入 64 位整数
           write(f,htol(Int64(42)))
       end
8

julia> open(fname,"r") do f
           # 转换回主机字节顺序和主机整数类型
           Int(ltoh(read(f,Int64)))
       end
42
```

合并写入调用：

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."

julia> write(io, "Sometimes those members") + write(io, " write documentation.")
44

julia> String(take!(io))
"Sometimes those members write documentation."
```

没有 `write` 方法的用户定义的简单数据类型可以在 `Ref` 中包装后写入：

```jldoctest
julia> struct MyStruct; x::Float64; end

julia> io = IOBuffer()
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=Inf, ptr=1, mark=-1)

julia> write(io, Ref(MyStruct(42.0)))
8

julia> seekstart(io); read!(io, Ref(MyStruct(NaN)))
Base.RefValue{MyStruct}(MyStruct(42.0))
```
