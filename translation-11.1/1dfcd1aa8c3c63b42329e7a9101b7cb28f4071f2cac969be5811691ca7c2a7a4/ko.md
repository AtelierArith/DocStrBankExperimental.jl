```
popfirst!(collection) -> item
```

`collection`에서 첫 번째 `item`을 제거합니다.

이 함수는 많은 다른 프로그래밍 언어에서 `shift`라고 불립니다.

참고: [`pop!`](@ref), [`popat!`](@ref), [`delete!`](@ref).

# 예제

```jldoctest
julia> A = [1, 2, 3, 4, 5, 6]
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> popfirst!(A)
1

julia> A
5-element Vector{Int64}:
 2
 3
 4
 5
 6
```
