```
first(coll)
```

반복 가능한 컬렉션의 첫 번째 요소를 가져옵니다. 비어 있더라도 [`AbstractRange`](@ref)의 시작점을 반환합니다.

참고: [`only`](@ref), [`firstindex`](@ref), [`last`](@ref).

# 예제

```jldoctest
julia> first(2:2:10)
2

julia> first([1; 2; 3; 4])
1
```
