```
Base.rest(collection[, itr_state])
```

특정 반복 상태 `itr_state`에서 시작하여 `collection`의 꼬리를 가져오는 일반 함수입니다. `collection`이 `Tuple`인 경우 `Tuple`을 반환하고, `collection`이 `AbstractArray`인 경우 `AbstractVector`의 하위 유형을 반환하며, `collection`이 `AbstractString`인 경우 `AbstractString`의 하위 유형을 반환하고, 그렇지 않으면 임의의 반복자를 반환하며 `Iterators.rest(collection[, itr_state])`로 대체됩니다.

사용자 정의 컬렉션 유형에 대해 오버로드하여 최종 위치에서 [할당 시 슬러핑](@ref destructuring-assignment)의 동작을 사용자 지정할 수 있습니다. 예: `a, b... = collection`.

!!! compat "Julia 1.6"
    `Base.rest`는 최소한 Julia 1.6이 필요합니다.


참고: [`first`](@ref first), [`Iterators.rest`](@ref), [`Base.split_rest`](@ref).

# 예제

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.rest(a, state)
(1, [3, 2, 4])
```
