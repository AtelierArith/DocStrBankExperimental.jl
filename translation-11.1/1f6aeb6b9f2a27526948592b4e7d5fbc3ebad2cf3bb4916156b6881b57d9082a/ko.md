```
firstindex(collection) -> 정수
firstindex(collection, d) -> 정수
```

`collection`의 첫 번째 인덱스를 반환합니다. `d`가 주어지면, 차원 `d`에서 `collection`의 첫 번째 인덱스를 반환합니다.

구문 `A[begin]` 및 `A[1, begin]`은 각각 `A[firstindex(A)]` 및 `A[1, firstindex(A, 2)]`로 변환됩니다.

참고: [`first`](@ref), [`axes`](@ref), [`lastindex`](@ref), [`nextind`](@ref).

# 예제

```jldoctest
julia> firstindex([1,2,4])
1

julia> firstindex(rand(3,4,5), 2)
1
```
