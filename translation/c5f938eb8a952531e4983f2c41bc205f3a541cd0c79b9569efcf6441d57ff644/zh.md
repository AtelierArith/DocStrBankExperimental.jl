```
PipeBuffer(data::AbstractVector{UInt8}=UInt8[]; maxsize::Integer = typemax(Int))
```

一个 [`IOBuffer`](@ref)，允许通过追加的方式进行读取和写入。不支持寻址和截断。有关可用构造函数，请参见 [`IOBuffer`](@ref)。如果提供了 `data`，则创建一个 `PipeBuffer` 以在数据向量上操作， optionally 指定一个大小，超出该大小底层的 `Array` 可能无法增长。
