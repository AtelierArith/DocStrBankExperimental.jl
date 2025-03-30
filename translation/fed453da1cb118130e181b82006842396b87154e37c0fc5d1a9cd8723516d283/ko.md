```
isspace(c::AbstractChar) -> Bool
```

문자가 공백 문자 중 하나인지 테스트합니다. ASCII 문자 '\t', '\n', '\v', '\f', '\r', 및 ' ', 라틴-1 문자 U+0085, 그리고 유니코드 범주 Zs의 문자를 포함합니다.

# 예제

```jldoctest
julia> isspace('\n')
true

julia> isspace('\r')
true

julia> isspace(' ')
true

julia> isspace('\x20')
true
```
