```
strip([pred=isspace,] str::AbstractString) -> SubString
strip(str::AbstractString, chars) -> SubString
```

`str`에서 선행 및 후행 문자를 제거합니다. 제거할 문자는 `chars`로 지정되거나, 함수 `pred`가 `true`를 반환하는 문자입니다.

기본 동작은 선행 및 후행 공백과 구분 기호를 제거하는 것입니다: 정확한 세부 사항은 [`isspace`](@ref)를 참조하십시오.

선택적 `chars` 인수는 제거할 문자를 지정합니다: 단일 문자, 문자 벡터 또는 문자 집합일 수 있습니다.

또한 [`lstrip`](@ref) 및 [`rstrip`](@ref)를 참조하십시오.

!!! compat "Julia 1.2"
    함수가 예측 함수(predicate function)를 수용하는 메서드는 Julia 1.2 이상이 필요합니다.


# 예제

```jldoctest
julia> strip("{3, 5}\n", ['{', '}', '\n'])
"3, 5"
```
