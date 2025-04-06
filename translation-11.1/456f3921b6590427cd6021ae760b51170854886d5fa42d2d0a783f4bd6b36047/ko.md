```
last(coll)
```

정렬된 컬렉션의 마지막 요소를 가져옵니다. O(1) 시간 내에 계산할 수 있는 경우에 해당합니다. 이는 [`lastindex`](@ref)를 호출하여 마지막 인덱스를 가져오는 방식으로 수행됩니다. 비어 있더라도 [`AbstractRange`](@ref)의 끝점을 반환합니다.

또한 [`first`](@ref), [`endswith`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> last(1:2:10)
9

julia> last([1; 2; 3; 4])
4
```
