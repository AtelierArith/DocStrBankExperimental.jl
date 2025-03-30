```
filter(f, a)
```

컬렉션 `a`의 복사본을 반환하며, `f`가 `false`인 요소를 제거합니다. 함수 `f`는 하나의 인수를 받습니다.

!!! compat "Julia 1.4"
    `a`를 튜플로 지원하려면 최소한 Julia 1.4가 필요합니다.


참고: [`filter!`](@ref), [`Iterators.filter`](@ref).

# 예제

```jldoctest
julia> a = 1:10
1:10

julia> filter(isodd, a)
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
