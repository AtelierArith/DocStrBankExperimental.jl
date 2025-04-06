```
eachsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

`str`를 구분자 `dlm`의 발생에 따라 나누고 부분 문자열에 대한 반복자를 반환합니다. `dlm`은 [`findnext`](@ref)의 첫 번째 인수로 허용되는 형식(즉, 문자열, 정규 표현식 또는 함수) 중 하나이거나 단일 문자 또는 문자 모음일 수 있습니다.

`dlm`이 생략되면 기본값은 [`isspace`](@ref)입니다.

선택적 키워드 인수는 다음과 같습니다:

  * `limit`: 결과의 최대 크기. `limit=0`은 최대 없음(기본값)을 의미합니다.
  * `keepempty`: 빈 필드를 결과에 포함할지 여부. `dlm` 인수가 없으면 기본값은 `false`, `dlm` 인수가 있으면 `true`입니다.

자세한 내용은 [`split`](@ref)를 참조하세요.

!!! compat "Julia 1.8"
    `eachsplit` 함수는 최소한 Julia 1.8이 필요합니다.


# 예제

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> b = eachsplit(a, ".")
Base.SplitIterator{String, String}("Ma.rch", ".", 0, true)

julia> collect(b)
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
