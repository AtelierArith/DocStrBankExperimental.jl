```
isless(a::AbstractString, b::AbstractString) -> Bool
```

문자열 `a`가 문자열 `b`보다 알파벳 순서(정확히는 유니코드 코드 포인트에 의한 사전 순서)에서 먼저 오는지 테스트합니다.

# 예제

```jldoctest
julia> isless("a", "b")
true

julia> isless("β", "α")
false

julia> isless("a", "a")
false
```
