```
count(
    pattern::Union{AbstractChar,AbstractString,AbstractPattern},
    string::AbstractString;
    overlap::Bool = false,
)
```

`pattern`이 `string`에서 일치하는 횟수를 반환합니다. 이는 `length(findall(pattern, string))`를 호출하는 것과 동일하지만 더 효율적입니다.

`overlap=true`인 경우, 일치하는 시퀀스는 원래 문자열의 인덱스에서 겹칠 수 있지만, 그렇지 않으면 서로 다른 문자 범위에서 나와야 합니다.

!!! compat "Julia 1.3"
    이 메서드는 최소한 Julia 1.3이 필요합니다.


!!! compat "Julia 1.7"
    패턴으로 문자를 사용하는 것은 최소한 Julia 1.7이 필요합니다.


# 예제

```jldoctest
julia> count('a', "JuliaLang")
2

julia> count(r"a(.)a", "cabacabac", overlap=true)
3

julia> count(r"a(.)a", "cabacabac")
2
```
