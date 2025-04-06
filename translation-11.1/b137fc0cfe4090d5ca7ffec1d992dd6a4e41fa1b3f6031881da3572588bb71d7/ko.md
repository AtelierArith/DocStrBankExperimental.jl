```
findprev(pattern::AbstractString, string::AbstractString, start::Integer)
```

`string`에서 `start` 위치에서 시작하여 `pattern`의 이전 발생을 찾습니다.

반환 값은 일치하는 시퀀스가 발견된 인덱스의 범위로, `s[findprev(x, s, i)] == x`가 성립합니다:

`findprev("substring", string, i)` == `start:stop`로, `string[start:stop] == "substring"`이고 `stop <= i`이거나, 일치하지 않으면 `nothing`입니다.

# 예제

```jldoctest
julia> findprev("z", "Hello to the world", 18) === nothing
true

julia> findprev("o", "Hello to the world", 18)
15:15

julia> findprev("Julia", "JuliaLang", 6)
1:5
```
