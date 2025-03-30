```
peek(stream[, T=UInt8])
```

스트림에서 현재 위치를 이동하지 않고 타입 `T`의 값을 읽고 반환합니다. 또한 [`startswith(stream, char_or_string)`](@ref)를 참조하십시오.

# 예제

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
    타입을 수용하는 메서드는 Julia 1.5 이상이 필요합니다.

