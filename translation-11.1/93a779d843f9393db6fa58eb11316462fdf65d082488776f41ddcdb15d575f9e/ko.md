```
lastindex(collection) -> Integer
lastindex(collection, d) -> Integer
```

`collection`의 마지막 인덱스를 반환합니다. `d`가 주어지면, 차원 `d`에서 `collection`의 마지막 인덱스를 반환합니다.

구문 `A[end]`와 `A[end, end]`는 각각 `A[lastindex(A)]`와 `A[lastindex(A, 1), lastindex(A, 2)]`로 변환됩니다.

참고: [`axes`](@ref), [`firstindex`](@ref), [`eachindex`](@ref), [`prevind`](@ref).

# 예제

```jldoctest
julia> lastindex([1,2,4])
3

julia> lastindex(rand(3,4,5), 2)
4
```
