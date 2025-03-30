```
Base.split_rest(collection, n::Int[, itr_state]) -> (rest_but_n, last_n)
```

특정 반복 상태 `itr_state`에서 시작하여 `collection`의 꼬리를 분할하는 일반 함수입니다. 두 개의 새로운 컬렉션으로 구성된 튜플을 반환합니다. 첫 번째 컬렉션은 마지막 `n`개의 요소를 제외한 꼬리의 모든 요소를 포함하고, 두 번째 컬렉션은 마지막 `n`개의 요소로 구성됩니다.

첫 번째 컬렉션의 유형은 일반적으로 [`Base.rest`](@ref)의 유형을 따르지만, 기본 사례는 게으르지 않고 벡터로 즉시 수집됩니다.

사용자 정의 컬렉션 유형에 대해 오버로드할 수 있으며, 이는 비최종 위치에서 [할당 시 슬러핑](@ref destructuring-assignment)의 동작을 사용자 정의하는 데 사용됩니다. 예: `a, b..., c = collection`.

!!! compat "Julia 1.9"
    `Base.split_rest`는 최소한 Julia 1.9가 필요합니다.


참고: [`Base.rest`](@ref).

# 예제

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> first, state = iterate(a)
(1, 2)

julia> first, Base.split_rest(a, 1, state)
(1, ([3, 2], [4]))
```
