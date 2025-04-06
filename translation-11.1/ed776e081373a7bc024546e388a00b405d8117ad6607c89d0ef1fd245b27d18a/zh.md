```
peek(stream[, T=UInt8])
```

从流中读取并返回类型 `T` 的值，而不推进流中的当前位置。另见 [`startswith(stream, char_or_string)`](@ref)。

# 示例

```jldoctest
julia> b = IOBuffer("julia");

julia> peek(b)
0x6a

julia> position(b)
0

julia> peek(b, Char)
'j': ASCII/Unicode U+006A (category Ll: Letter, lowercase)
```

!!! compat "Julia 1.5"
    接受类型的方法需要 Julia 1.5 或更高版本。

