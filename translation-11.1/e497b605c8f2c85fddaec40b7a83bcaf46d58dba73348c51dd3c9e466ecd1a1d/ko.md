```
uppercasefirst(s::AbstractString) -> String
```

`s`의 첫 번째 문자를 대문자로 변환하여 반환합니다(기술적으로는 유니코드에 대한 "타이틀 케이스"). `s`의 모든 단어의 첫 번째 문자를 대문자로 만들려면 [`titlecase`](@ref)를 참조하십시오.

또한 [`lowercasefirst`](@ref), [`uppercase`](@ref), [`lowercase`](@ref), [`titlecase`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> uppercasefirst("python")
"Python"
```
