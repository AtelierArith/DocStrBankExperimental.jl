```
codeunit(s::AbstractString) -> Type{<:Union{UInt8, UInt16, UInt32}}
```

返回给定字符串对象的代码单元类型。对于 ASCII、Latin-1 或 UTF-8 编码的字符串，这将是 `UInt8`；对于 UCS-2 和 UTF-16，它将是 `UInt16`；对于 UTF-32，它将是 `UInt32`。代码单元类型不必仅限于这三种类型，但很难想到不使用这些单位的广泛使用的字符串编码。当 `s` 是一个非空字符串时，`codeunit(s)` 与 `typeof(codeunit(s,1))` 是相同的。

另请参见 [`ncodeunits`](@ref)。
