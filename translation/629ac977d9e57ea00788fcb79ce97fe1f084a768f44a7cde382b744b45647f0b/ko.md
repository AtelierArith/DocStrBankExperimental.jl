```
base64decode(string)
```

base64로 인코딩된 `string`을 디코딩하고 디코딩된 바이트의 `Vector{UInt8}`를 반환합니다.

자세한 내용은 [`base64encode`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> b = base64decode("SGVsbG8h")
6-element Vector{UInt8}:
 0x48
 0x65
 0x6c
 0x6c
 0x6f
 0x21

julia> String(b)
"Hello!"
```
