```
findnext(pattern::AbstractString, string::AbstractString, start::Integer)
findnext(pattern::AbstractPattern, string::String, start::Integer)
```

`string`에서 `start` 위치에서 시작하여 `pattern`의 다음 발생을 찾습니다. `pattern`은 문자열이거나 정규 표현식일 수 있으며, 이 경우 `string`은 `String` 유형이어야 합니다.

반환 값은 일치하는 시퀀스가 발견된 인덱스의 범위로, `s[findnext(x, s, i)] == x`가 성립합니다:

`findnext("substring", string, i)` == `start:stop`로, `string[start:stop] == "substring"`이고 `i <= start`이거나, 일치하지 않으면 `nothing`입니다.

# 예제

```jldoctest
julia> findnext("z", "Hello to the world", 1) === nothing
true

julia> findnext("o", "Hello to the world", 6)
8:8

julia> findnext("Lang", "JuliaLang", 2)
6:9
```
