```
isvalid(T, value) -> Bool
```

주어진 값이 해당 유형에 대해 유효하면 `true`를 반환합니다. 현재 유형은 `AbstractChar` 또는 `String`일 수 있습니다. `AbstractChar`의 값은 `AbstractChar` 유형이거나 [`UInt32`](@ref)일 수 있습니다. `String`의 값은 해당 유형, `SubString{String}`, `Vector{UInt8}` 또는 그 연속 하위 배열일 수 있습니다.

# 예시

```jldoctest
julia> isvalid(Char, 0xd800)
false

julia> isvalid(String, SubString("thisisvalid",1,5))
true

julia> isvalid(Char, 0xd799)
true
```

!!! compat "Julia 1.6"
    하위 배열 값에 대한 지원은 Julia 1.6에서 추가되었습니다.

