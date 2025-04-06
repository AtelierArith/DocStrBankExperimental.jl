```
*(s::Union{AbstractString, AbstractChar}, t::Union{AbstractString, AbstractChar}...) -> AbstractString
```

문자열 및/또는 문자를 연결하여 [`String`](@ref) 또는 [`AnnotatedString`](@ref) (적절한 경우) 를 생성합니다. 이는 인수에 대해 [`string`](@ref) 또는 [`annotatedstring`](@ref) 함수를 호출하는 것과 동일합니다. 내장 문자열 유형의 연결은 항상 `String` 유형의 값을 생성하지만, 다른 문자열 유형은 적절한 경우 다른 유형의 문자열을 반환하도록 선택할 수 있습니다.

# 예제

```jldoctest
julia> "Hello " * "world"
"Hello world"

julia> 'j' * "ulia"
"julia"
```
