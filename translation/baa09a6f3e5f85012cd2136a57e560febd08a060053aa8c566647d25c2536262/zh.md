```
reinterpret(::Type{Out}, x::In)
```

将二进制数据中 isbits 值 `x` 的类型解释更改为 isbits 类型 `Out`。`Out` 的大小（忽略填充）必须与 `x` 的类型大小相同。例如，`reinterpret(Float32, UInt32(7))` 将与 `UInt32(7)` 对应的 4 个字节解释为 [`Float32`](@ref)。注意 `reinterpret(In, reinterpret(Out, x)) === x`

```jldoctest
julia> reinterpret(Float32, UInt32(7))
1.0f-44

julia> reinterpret(NTuple{2, UInt8}, 0x1234)
(0x34, 0x12)

julia> reinterpret(UInt16, (0x34, 0x12))
0x1234

julia> reinterpret(Tuple{UInt16, UInt8}, (0x01, 0x0203))
(0x0301, 0x02)
```

!!! note
    填充的处理与 reinterpret(::DataType, ::AbstractArray) 不同。


!!! warning
    如果 `Out` 中某些位的组合被认为无效，并且类型的构造函数和方法会阻止这些组合，请谨慎使用。没有额外验证可能会导致意外行为。

