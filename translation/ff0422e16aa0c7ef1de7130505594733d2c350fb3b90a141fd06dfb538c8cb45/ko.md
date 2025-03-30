```
isdisjoint(a, b) -> Bool
```

컬렉션 `a`와 `b`가 서로 겹치지 않는지 확인합니다. `isempty(a ∩ b)`와 동등하지만 가능한 경우 더 효율적입니다.

참고: [`intersect`](@ref), [`isempty`](@ref), [`issetequal`](@ref).

!!! compat "Julia 1.5"
    이 함수는 최소한 Julia 1.5가 필요합니다.


# 예제

```jldoctest
julia> isdisjoint([1, 2], [2, 3, 4])
false

julia> isdisjoint([3, 1], [2, 4])
true
```
