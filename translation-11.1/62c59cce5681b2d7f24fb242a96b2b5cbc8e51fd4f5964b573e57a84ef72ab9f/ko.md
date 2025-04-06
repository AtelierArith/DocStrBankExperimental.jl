```
ispunct(c::AbstractChar) -> Bool
```

문자가 유니코드 일반 범주 구두점에 속하는지 여부를 테스트합니다. 즉, 범주 코드가 'P'로 시작하는 문자입니다.

# 예제

```jldoctest
julia> ispunct('α')
false

julia> ispunct('/')
true

julia> ispunct(';')
true
```
