```
findmin(itr) -> (x, index)
```

컬렉션 `itr`의 최소 요소와 그 인덱스 또는 키를 반환합니다. 최소 요소가 여러 개일 경우, 첫 번째 요소가 반환됩니다. `NaN`은 `missing`을 제외한 모든 값보다 작게 처리됩니다.

인덱스는 [`keys(itr)`](@ref) 및 [`pairs(itr)`](@ref)에서 반환되는 것과 동일한 유형입니다.

참고: [`findmax`](@ref), [`argmin`](@ref), [`minimum`](@ref).

# 예제

```jldoctest
julia> findmin([8, 0.1, -9, pi])
(-9.0, 3)

julia> findmin([1, 7, 7, 6])
(1, 1)

julia> findmin([1, 7, 7, NaN])
(NaN, 4)
```
