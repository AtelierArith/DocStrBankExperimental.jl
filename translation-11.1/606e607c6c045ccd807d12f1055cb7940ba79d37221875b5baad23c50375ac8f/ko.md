```
ncodeunits(s::AbstractString) -> Int
```

문자열의 코드 유닛 수를 반환합니다. 이 문자열에 접근하기 위한 인덱스는 `1 ≤ i ≤ ncodeunits(s)`를 만족해야 합니다. 이러한 인덱스가 모두 유효한 것은 아니며, 문자 시작이 아닐 수도 있지만 `codeunit(s,i)`를 호출할 때 코드 유닛 값을 반환합니다.

# 예제

```jldoctest
julia> ncodeunits("The Julia Language")
18

julia> ncodeunits("∫eˣ")
6

julia> ncodeunits('∫'), ncodeunits('e'), ncodeunits('ˣ')
(3, 1, 2)
```

또한 [`codeunit`](@ref), [`checkbounds`](@ref), [`sizeof`](@ref), [`length`](@ref), [`lastindex`](@ref)를 참조하세요.
