```
isxdigit(c::AbstractChar) -> Bool
```

문자가 유효한 16진수 숫자인지 테스트합니다. 여기에는 `0x` 접두사에서의 `x`는 포함되지 않습니다.

# 예제

```jldoctest
julia> isxdigit('a')
true

julia> isxdigit('x')
false
```
