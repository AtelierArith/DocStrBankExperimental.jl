```
isempty(collection) -> Bool
```

컬렉션이 비어 있는지(요소가 없는지) 확인합니다.

!!! 경고     `isempty(itr)`는 적절한 [`Base.isdone(itr)`](@ref) 메서드가 정의되지 않은 경우 상태가 있는 반복자 `itr`의 다음 요소를 소비할 수 있습니다. 상태가 있는 반복자는 *isdone*을 구현해야 하지만, 모든 반복자 유형을 지원해야 하는 일반 코드를 작성할 때 `isempty` 사용을 피하고 싶을 수 있습니다.

# 예제

```jldoctest
julia> isempty([])
true

julia> isempty([1 2 3])
false
```
