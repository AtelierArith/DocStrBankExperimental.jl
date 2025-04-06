```
iscntrl(c::AbstractChar) -> Bool
```

문자가 제어 문자(control character)인지 테스트합니다. 제어 문자는 유니코드의 라틴-1 하위 집합에 있는 비인쇄 문자입니다.

# 예제

```jldoctest
julia> iscntrl('\x01')
true

julia> iscntrl('a')
false
```
