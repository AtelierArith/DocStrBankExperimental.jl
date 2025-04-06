```
max(x, y, ...)
```

인수의 최대값을 [`isless`](@ref)에 따라 반환합니다. 인수 중 하나라도 [`missing`](@ref)인 경우 `missing`을 반환합니다. 컬렉션에서 최대 요소를 가져오는 [`maximum`](@ref) 함수도 참조하십시오.

# 예제

```jldoctest
julia> max(2, 5, 1)
5

julia> max(5, missing, 6)
missing
```
