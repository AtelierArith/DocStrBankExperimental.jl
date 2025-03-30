```
eachrsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachrsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

`str`를 구분 기호 `dlm`으로 나누어 생성된 `SubString`의 반복자를 반환하며, 결과는 역순(오른쪽에서 왼쪽으로)으로 제공됩니다. `dlm`은 [`findprev`](@ref)의 첫 번째 인수로 허용되는 형식(즉, 문자열, 단일 문자 또는 함수) 중 하나이거나 문자 집합일 수 있습니다.

`dlm`이 생략되면 기본값은 [`isspace`](@ref)이며, `keepempty`의 기본값은 `false`입니다.

선택적 키워드 인수는 다음과 같습니다:

  * `limit > 0`인 경우, 반복자는 최대 `limit - 1`회만 나누고 나머지 문자열은 나누지 않고 반환합니다. `limit < 1`은 나누기에 대한 제한이 없음을 의미합니다(기본값).
  * `keepempty`: 반복할 때 빈 필드를 반환할지 여부 기본값은 `dlm` 인수가 없는 경우 `false`, `dlm` 인수가 있는 경우 `true`입니다.

[`split`](@ref)와는 달리, [`rsplit`](@ref) 및 [`eachsplit`](@ref)와 이 함수는 입력에서 발생하는 대로 부분 문자열을 오른쪽에서 왼쪽으로 반복합니다.

또한 [`eachsplit`](@ref), [`rsplit`](@ref)를 참조하십시오.

!!! compat "Julia 1.11"
    이 함수는 Julia 1.11 이상이 필요합니다.


# 예제

```jldoctest
julia> a = "Ma.r.ch";

julia> collect(eachrsplit(a, ".")) == ["ch", "r", "Ma"]
true

julia> collect(eachrsplit(a, "."; limit=2)) == ["ch", "Ma.r"]
true
```
