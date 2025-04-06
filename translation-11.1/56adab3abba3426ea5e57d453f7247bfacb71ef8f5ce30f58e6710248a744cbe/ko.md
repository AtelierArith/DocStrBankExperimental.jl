```
findnext(ch::AbstractChar, string::AbstractString, start::Integer)
```

문자 `ch`의 다음 발생을 `start` 위치에서 시작하여 `string`에서 찾습니다.

!!! compat "Julia 1.3"
    이 메서드는 최소한 Julia 1.3이 필요합니다.


# 예제

```jldoctest
julia> findnext('z', "Hello to the world", 1) === nothing
true

julia> findnext('o', "Hello to the world", 6)
8
```
