```
iszero(x)
```

`x == zero(x)`이면 `true`를 반환합니다. `x`가 배열인 경우, 이는 `x`의 모든 요소가 0인지 확인합니다.

참고: [`isone`](@ref), [`isinteger`](@ref), [`isfinite`](@ref), [`isnan`](@ref).

# 예제

```jldoctest
julia> iszero(0.0)
true

julia> iszero([1, 9, 0])
false

julia> iszero([false, 0, 0])
true
```
