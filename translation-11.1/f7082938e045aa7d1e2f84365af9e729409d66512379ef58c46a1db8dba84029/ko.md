```
SubString(s::AbstractString, i::Integer, j::Integer=lastindex(s))
SubString(s::AbstractString, r::UnitRange{<:Integer})
```

[`getindex`](@ref)와 유사하지만, 복사본을 만드는 대신 범위 `i:j` 또는 `r` 내에서 부모 문자열 `s`에 대한 뷰를 반환합니다.

[`@views`](@ref) 매크로는 코드 블록 내의 모든 문자열 슬라이스 `s[i:j]`를 서브스트링 `SubString(s, i, j)`으로 변환합니다.

# 예제

```jldoctest
julia> SubString("abc", 1, 2)
"ab"

julia> SubString("abc", 1:2)
"ab"

julia> SubString("abc", 2)
"bc"
```
