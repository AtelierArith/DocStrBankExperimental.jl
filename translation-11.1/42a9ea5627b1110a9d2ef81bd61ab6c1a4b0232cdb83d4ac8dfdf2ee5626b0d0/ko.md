```
unique(itr)
```

컬렉션 `itr`의 고유한 요소만 포함하는 배열을 반환합니다. 이는 [`isequal`](@ref) 및 [`hash`](@ref)에 의해 결정되며, 동등한 요소 집합의 첫 번째 요소가 원래 나타나는 순서로 정렬됩니다. 입력의 요소 유형은 유지됩니다.

참고: [`unique!`](@ref), [`allunique`](@ref), [`allequal`](@ref).

# 예제

```jldoctest
julia> unique([1, 2, 6, 2])
3-element Vector{Int64}:
 1
 2
 6

julia> unique(Real[1, 1.0, 2])
2-element Vector{Real}:
 1
 2
```
