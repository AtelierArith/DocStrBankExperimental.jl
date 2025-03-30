```
mmap(io::Union{IOStream,AbstractString,Mmap.AnonymousMmap}[, type::Type{Array{T,N}}, dims, offset]; grow::Bool=true, shared::Bool=true)
mmap(type::Type{Array{T,N}}, dims)
```

创建一个与文件链接的 `Array`，使用内存映射。这提供了一种方便的方式来处理过大而无法放入计算机内存的数据。

类型是一个 `Array{T,N}`，其中 `T` 是位类型元素，`N` 是确定数组字节如何被解释的维度。请注意，文件必须以二进制格式存储，并且不支持格式转换（这是操作系统的限制，而不是 Julia 的限制）。

`dims` 是一个元组或单个 [`Integer`](@ref)，指定数组的大小或长度。

文件通过流参数传递，可以是打开的 [`IOStream`](@ref) 或文件名字符串。当您初始化流时，使用 `"r"` 表示“只读”数组，使用 `"w+"` 创建一个新的数组以将值写入磁盘。

如果未指定 `type` 参数，则默认值为 `Vector{UInt8}`。

可选地，您可以指定一个偏移量（以字节为单位），例如，如果您想跳过文件中的头部。偏移量的默认值是 `IOStream` 的当前流位置。

`grow` 关键字参数指定是否应扩展磁盘文件以适应请求的数组大小（如果总文件大小 < 请求的数组大小）。扩展文件需要写入权限。

`shared` 关键字参数指定结果 `Array` 及其所做的更改是否对映射同一文件的其他进程可见。

例如，以下代码

```julia
# 创建一个用于 mmapping 的文件
# （您也可以使用 mmap 来执行此步骤）
using Mmap
A = rand(1:20, 5, 30)
s = open("/tmp/mmap.bin", "w+")
# 我们将数组的维度写入文件的前两个 Ints
write(s, size(A,1))
write(s, size(A,2))
# 现在写入数据
write(s, A)
close(s)

# 通过读取它来测试
s = open("/tmp/mmap.bin")   # 默认是只读
m = read(s, Int)
n = read(s, Int)
A2 = mmap(s, Matrix{Int}, (m,n))
```

创建一个与流 `s` 关联的 `m` 行 `n` 列的 `Matrix{Int}`。

一个更便携的文件需要在头部编码字大小 – 32 位或 64 位 – 和字节序信息。在实践中，考虑使用标准格式（如 HDF5）编码二进制数据（可以与内存映射一起使用）。
