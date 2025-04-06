```
argmax(itr)
```

컬렉션에서 최대 요소의 인덱스 또는 키를 반환합니다. 최대 요소가 여러 개일 경우, 첫 번째 요소가 반환됩니다.

컬렉션은 비어 있지 않아야 합니다.

인덱스는 [`keys(itr)`](@ref) 및 [`pairs(itr)`](@ref)에서 반환되는 것과 동일한 유형입니다.

값은 `isless`로 비교됩니다.

참고: [`argmin`](@ref), [`findmax`](@ref).

# 예제

```jldoctest
julia> argmax([8, 0.1, -9, pi])
1

julia> argmax([1, 7, 7, 6])
2

julia> argmax([1, 7, 7, NaN])
4
```
