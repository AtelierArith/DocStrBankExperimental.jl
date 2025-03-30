```
allunique(itr) -> Bool
allunique(f, itr) -> Bool
```

`itr`의 모든 값이 [`isequal`](@ref)로 비교했을 때 서로 다르면 `true`를 반환합니다. 두 번째 방법의 경우 `[f(x) for x in itr]`의 모든 값이 서로 다르면 `true`를 반환합니다.

`allunique(f, itr)`는 `f`를 `length(itr)`보다 적은 횟수만큼 호출할 수 있습니다. 호출 횟수는 구현 세부사항으로 간주됩니다.

`allunique`는 입력이 정렬되어 있을 때 특수화된 구현을 사용할 수 있습니다.

참고: [`unique`](@ref), [`issorted`](@ref), [`allequal`](@ref).

!!! compat "Julia 1.11"
    `allunique(f, itr)` 메서드는 최소한 Julia 1.11이 필요합니다.


# 예제

```jldoctest
julia> allunique([1, 2, 3])
true

julia> allunique([1, 2, 1, 2])
false

julia> allunique(Real[1, 1.0, 2])
false

julia> allunique([NaN, 2.0, NaN, 4.0])
false

julia> allunique(abs, [1, -1, 2])
false
```
