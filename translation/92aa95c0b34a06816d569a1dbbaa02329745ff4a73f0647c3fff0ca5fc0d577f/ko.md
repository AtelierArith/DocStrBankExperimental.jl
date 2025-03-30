```
lowercase(s::AbstractString)
```

모든 문자를 소문자로 변환한 `s`를 반환합니다.

또한 [`uppercase`](@ref), [`titlecase`](@ref), [`lowercasefirst`](@ref)를 참조하세요.

# 예시

```jldoctest
julia> lowercase("STRINGS AND THINGS")
"strings and things"
```
