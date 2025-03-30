```
issetequal(a, b) -> Bool
```

`a`와 `b`가 동일한 요소를 가지고 있는지 확인합니다. `a ⊆ b && b ⊆ a`와 동등하지만 가능한 경우 더 효율적입니다.

참고: [`isdisjoint`](@ref), [`union`](@ref).

# 예제

```jldoctest
julia> issetequal([1, 2], [1, 2, 3])
false

julia> issetequal([1, 2], [2, 1])
true
```
