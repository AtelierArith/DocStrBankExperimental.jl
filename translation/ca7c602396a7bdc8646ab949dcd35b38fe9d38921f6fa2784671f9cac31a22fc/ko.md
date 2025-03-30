```
isascii(c::Union{AbstractChar,AbstractString}) -> Bool
```

문자가 ASCII 문자 집합에 속하는지, 또는 문자열의 모든 요소가 이 조건을 만족하는지 테스트합니다.

# 예제

```jldoctest
julia> isascii('a')
true

julia> isascii('α')
false

julia> isascii("abc")
true

julia> isascii("αβγ")
false
```

예를 들어, `isascii`는 [`filter`](@ref) 또는 [`replace`](@ref)와 같은 함수의 조건 함수로 사용되어 비ASCII 문자를 각각 제거하거나 대체하는 데 사용할 수 있습니다:

```jldoctest
julia> filter(isascii, "abcdeγfgh") # 비ASCII 문자를 버림
"abcdefgh"

julia> replace("abcdeγfgh", !isascii=>' ') # 비ASCII 문자를 공백으로 대체
"abcde fgh"
```
