```
chop(s::AbstractString; head::Integer = 0, tail::Integer = 1)
```

`s`에서 처음 `head`와 마지막 `tail` 문자를 제거합니다. 호출 `chop(s)`는 `s`의 마지막 문자를 제거합니다. `length(s)`보다 더 많은 문자를 제거하도록 요청하면 빈 문자열이 반환됩니다.

또한 [`chomp`](@ref), [`startswith`](@ref), [`first`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> a = "March"
"March"

julia> chop(a)
"Marc"

julia> chop(a, head = 1, tail = 2)
"ar"

julia> chop(a, head = 5, tail = 5)
""
```
