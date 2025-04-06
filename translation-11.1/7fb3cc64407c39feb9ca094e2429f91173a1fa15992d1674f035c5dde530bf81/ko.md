```
findmax(itr) -> (x, index)
```

컬렉션 `itr`의 최대 요소와 그 인덱스 또는 키를 반환합니다. 최대 요소가 여러 개일 경우, 첫 번째 요소가 반환됩니다. 값은 `isless`로 비교됩니다.

인덱스는 [`keys(itr)`](@ref) 및 [`pairs(itr)`](@ref)에서 반환되는 것과 동일한 유형입니다.

참고: [`findmin`](@ref), [`argmax`](@ref), [`maximum`](@ref).

# 예제

```jldoctest
julia> findmax([8, 0.1, -9, pi])
(8.0, 1)

julia> findmax([1, 7, 7, 6])
(7, 2)

julia> findmax([1, 7, 7, NaN])
(NaN, 4)
```
