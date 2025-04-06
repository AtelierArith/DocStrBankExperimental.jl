```
isprint(c::AbstractChar) -> Bool
```

문자가 인쇄 가능한지 테스트하며, 공백을 포함하지만 제어 문자는 포함하지 않습니다.

# 예제

```jldoctest
julia> isprint('\x01')
false

julia> isprint('A')
true
```
