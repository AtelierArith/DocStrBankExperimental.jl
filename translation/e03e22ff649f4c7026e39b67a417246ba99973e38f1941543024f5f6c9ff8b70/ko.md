```
rstrip([pred=isspace,] str::AbstractString) -> SubString
rstrip(str::AbstractString, chars) -> SubString
```

`str`에서 후행 문자를 제거합니다. 이는 `chars`로 지정된 문자이거나 함수 `pred`가 `true`를 반환하는 문자입니다.

기본 동작은 후행 공백 및 구분 기호를 제거하는 것입니다: 정확한 세부 사항은 [`isspace`](@ref)를 참조하십시오.

선택적 `chars` 인수는 제거할 문자를 지정합니다: 단일 문자일 수도 있고, 문자 벡터 또는 집합일 수도 있습니다.

또한 [`strip`](@ref) 및 [`lstrip`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> a = rpad("March", 20)
"March               "

julia> rstrip(a)
"March"
```
