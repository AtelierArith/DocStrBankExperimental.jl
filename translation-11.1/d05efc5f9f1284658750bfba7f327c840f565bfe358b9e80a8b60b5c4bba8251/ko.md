```
argmin(itr)
```

컬렉션에서 최소 요소의 인덱스 또는 키를 반환합니다. 최소 요소가 여러 개 있는 경우 첫 번째 요소가 반환됩니다.

컬렉션은 비어 있지 않아야 합니다.

인덱스는 [`keys(itr)`](@ref) 및 [`pairs(itr)`](@ref)에서 반환된 것과 동일한 유형입니다.

`NaN`은 `missing`을 제외한 모든 값보다 작게 처리됩니다.

참고: [`argmax`](@ref), [`findmin`](@ref).

# 예제

```jldoctest
julia> argmin([8, 0.1, -9, pi])
3

julia> argmin([7, 1, 1, 6])
2

julia> argmin([7, 1, 1, NaN])
4
```
