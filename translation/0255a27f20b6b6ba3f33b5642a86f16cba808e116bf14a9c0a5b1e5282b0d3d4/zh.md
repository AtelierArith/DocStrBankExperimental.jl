```
reinterpret(T::DataType, A::AbstractArray)
```

构造一个数组的视图，该视图具有与给定数组相同的二进制数据，但元素类型为 `T`。

此函数也适用于“惰性”数组，其元素在被显式检索之前不会被计算。例如，在范围 `1:6` 上使用 `reinterpret` 的效果与在稠密向量 `collect(1:6)` 上的效果类似：

```jldoctest
julia> reinterpret(Float32, UInt32[1 2 3 4 5])
1×5 reinterpret(Float32, ::Matrix{UInt32}):
 1.0f-45  3.0f-45  4.0f-45  6.0f-45  7.0f-45

julia> reinterpret(Complex{Int}, 1:6)
3-element reinterpret(Complex{Int64}, ::UnitRange{Int64}):
 1 + 2im
 3 + 4im
 5 + 6im
```

如果填充位的位置在 `T` 和 `eltype(A)` 之间不对齐，则结果数组将是只读或只写的，以防止无效位被写入或读取。

```jldoctest
julia> a = reinterpret(Tuple{UInt8, UInt32}, UInt32[1, 2])
1-element reinterpret(Tuple{UInt8, UInt32}, ::Vector{UInt32}):
 (0x01, 0x00000002)

julia> a[1] = 3
ERROR: 类型 Tuple{UInt8, UInt32} 的填充与类型 UInt32 不兼容。

julia> b = reinterpret(UInt32, Tuple{UInt8, UInt32}[(0x01, 0x00000002)]); # 显示将出错

julia> b[1]
ERROR: 类型 UInt32 的填充与类型 Tuple{UInt8, UInt32} 不兼容。
```
