```
match(r::Regex, s::AbstractString[, idx::Integer[, addopts]])
```

정규 표현식 `r`의 첫 번째 일치를 `s`에서 검색하고, 일치하는 경우를 포함하는 [`RegexMatch`](@ref) 객체를 반환합니다. 일치하지 않으면 아무것도 반환하지 않습니다. 일치하는 하위 문자열은 `m.match`에 접근하여 검색할 수 있으며, 캡처된 시퀀스는 `m.captures`에 접근하여 검색할 수 있습니다. 선택적 `idx` 인수는 검색을 시작할 인덱스를 지정합니다.

# 예제

```jldoctest
julia> rx = r"a(.)a"
r"a(.)a"

julia> m = match(rx, "cabac")
RegexMatch("aba", 1="b")

julia> m.captures
1-element Vector{Union{Nothing, SubString{String}}}:
 "b"

julia> m.match
"aba"

julia> match(rx, "cabac", 3) === nothing
true
```
