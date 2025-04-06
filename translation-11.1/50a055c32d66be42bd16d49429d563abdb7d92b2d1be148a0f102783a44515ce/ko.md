```
isvalid(value) -> Bool
```

주어진 값이 현재 `AbstractChar` 또는 `String` 또는 `SubString{String}`일 수 있는 해당 유형에 대해 유효하면 `true`를 반환합니다.

# 예시

```jldoctest
julia> isvalid(Char(0xd800))
false

julia> isvalid(SubString(String(UInt8[0xfe,0x80,0x80,0x80,0x80,0x80]),1,2))
false

julia> isvalid(Char(0xd799))
true
```
