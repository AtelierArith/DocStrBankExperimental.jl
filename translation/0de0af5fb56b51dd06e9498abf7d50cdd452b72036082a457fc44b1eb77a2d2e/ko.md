```
codeunit(s::AbstractString, i::Integer) -> Union{UInt8, UInt16, UInt32}
```

문자열 `s`에서 인덱스 `i`에 있는 코드 유닛 값을 반환합니다. 다음과 같은 점에 유의하세요.

```
codeunit(s, i) :: codeunit(s)
```

즉, `codeunit(s, i)`가 반환하는 값은 `codeunit(s)`가 반환하는 타입입니다.

# 예제

```jldoctest
julia> a = codeunit("Hello", 2)
0x65

julia> typeof(a)
UInt8
```

또한 [`ncodeunits`](@ref), [`checkbounds`](@ref)를 참조하세요.
