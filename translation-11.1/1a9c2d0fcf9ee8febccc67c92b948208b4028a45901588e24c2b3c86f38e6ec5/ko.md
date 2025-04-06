```
isequal_normalized(s1::AbstractString, s2::AbstractString; casefold=false, stripmark=false, chartransform=identity)
```

`s1`과 `s2`가 정규화된 동등한 유니코드 문자열인지 여부를 반환합니다. `casefold=true`인 경우 대소문자를 무시합니다(유니코드 대소문자 변환 수행); `stripmark=true`인 경우 발음 기호 및 기타 결합 문자를 제거합니다.

[`Unicode.normalize`](@ref)와 마찬가지로, `chartransform` 키워드를 통해 임의의 함수를 전달할 수 있습니다(정수 코드 포인트를 코드 포인트로 매핑하여) 사용자 정의 정규화를 수행할 수 있습니다. 예를 들어 [`Unicode.julia_chartransform`](@ref)와 같은 함수를 사용할 수 있습니다.

!!! compat "Julia 1.8"
    `isequal_normalized` 함수는 Julia 1.8에 추가되었습니다.


# 예제

예를 들어, 문자열 `"noël"`은 유니코드에서 두 가지 정규화된 동등한 방법으로 구성될 수 있습니다. 이는 `"ë"`가 단일 코드 포인트 U+00EB에서 형성되었는지, 아니면 ASCII 문자 `'e'` 다음에 U+0308 결합-다이아레시스 문자가 오는지에 따라 다릅니다.

```jldoctest
julia> s1 = "noël"
"noël"

julia> s2 = "noël"
"noël"

julia> s1 == s2
false

julia> isequal_normalized(s1, s2)
true

julia> isequal_normalized(s1, "noel", stripmark=true)
true

julia> isequal_normalized(s1, "NOËL", casefold=true)
true
```
