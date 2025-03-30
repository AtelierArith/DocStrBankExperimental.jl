```
allequal(itr) -> Bool
allequal(f, itr) -> Bool
```

`itr`의 모든 값이 [`isequal`](@ref)로 비교했을 때 같으면 `true`를 반환합니다. 두 번째 방법의 경우 `[f(x) for x in itr]`의 모든 값이 같으면 `true`를 반환합니다.

`allequal(f, itr)`는 `length(itr)`보다 적은 횟수로 `f`를 호출할 수 있습니다. 호출 횟수는 구현 세부사항으로 간주됩니다.

참고: [`unique`](@ref), [`allunique`](@ref).

!!! compat "Julia 1.8"
    `allequal` 함수는 최소한 Julia 1.8이 필요합니다.


!!! compat "Julia 1.11"
    메서드 `allequal(f, itr)`는 최소한 Julia 1.11이 필요합니다.


# 예제

```jldoctest
julia> allequal([])
true

julia> allequal([1])
true

julia> allequal([1, 1])
true

julia> allequal([1, 2])
false

julia> allequal(Dict(:a => 1, :b => 1))
false

julia> allequal(abs2, [1, -1])
true
```
