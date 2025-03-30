```
codeunit(s::AbstractString, i::Integer) -> Union{UInt8, UInt16, UInt32}
```

返回字符串 `s` 在索引 `i` 处的代码单元值。注意

```
codeunit(s, i) :: codeunit(s)
```

即 `codeunit(s, i)` 返回的值是 `codeunit(s)` 返回的类型。

# 示例

```jldoctest
julia> a = codeunit("Hello", 2)
0x65

julia> typeof(a)
UInt8
```

另请参见 [`ncodeunits`](@ref), [`checkbounds`](@ref).
