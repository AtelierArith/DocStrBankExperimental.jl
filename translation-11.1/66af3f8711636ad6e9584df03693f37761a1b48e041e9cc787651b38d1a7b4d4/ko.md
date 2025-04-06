```
min(x, y, ...)
```

인수의 최소값을 [`isless`](@ref)에 따라 반환합니다. 인수 중 하나라도 [`missing`](@ref)인 경우 `missing`을 반환합니다. 컬렉션에서 최소 요소를 가져오려면 [`minimum`](@ref) 함수를 참조하세요.

# 예제

```jldoctest
julia> min(2, 5, 1)
1

julia> min(4, missing, 6)
missing
```
