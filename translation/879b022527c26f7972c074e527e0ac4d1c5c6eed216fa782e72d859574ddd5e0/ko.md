```
eachmatch(r::Regex, s::AbstractString; overlap::Bool=false)
```

정규 표현식 `r`의 모든 일치를 문자열 `s`에서 검색하고 일치 항목에 대한 반복자를 반환합니다. `overlap`이 `true`인 경우, 일치하는 시퀀스는 원래 문자열의 인덱스에서 겹칠 수 있지만, 그렇지 않은 경우에는 서로 다른 문자 범위에서 가져와야 합니다.

# 예제

```jldoctest
julia> rx = r"a.a"
r"a.a"

julia> m = eachmatch(rx, "a1a2a3a")
Base.RegexMatchIterator{String}(r"a.a", "a1a2a3a", false)

julia> collect(m)
2-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a3a")

julia> collect(eachmatch(rx, "a1a2a3a", overlap = true))
3-element Vector{RegexMatch}:
 RegexMatch("a1a")
 RegexMatch("a2a")
 RegexMatch("a3a")
```
