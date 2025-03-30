```
==(a::AbstractString, b::AbstractString) -> Bool
```

두 문자열이 문자 단위(기술적으로는 유니코드 코드 포인트 단위)로 같은지 테스트합니다. 두 문자열 중 하나가 [`AnnotatedString`](@ref)인 경우 문자열 속성도 일치해야 합니다.

# 예시

```jldoctest
julia> "abc" == "abc"
true

julia> "abc" == "αβγ"
false
```
