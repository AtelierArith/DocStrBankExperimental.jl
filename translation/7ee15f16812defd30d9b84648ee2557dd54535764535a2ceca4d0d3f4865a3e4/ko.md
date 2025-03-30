```
clamp(x, lo, hi)
```

`lo <= x <= hi`인 경우 `x`를 반환합니다. `x > hi`인 경우 `hi`를 반환하고, `x < lo`인 경우 `lo`를 반환합니다. 인수는 공통 유형으로 승격됩니다.

자세한 내용은 [`clamp!`](@ref), [`min`](@ref), [`max`](@ref)를 참조하세요.

!!! compat "Julia 1.3"
    첫 번째 인수로 `missing`을 사용하려면 최소한 Julia 1.3이 필요합니다.


# 예제

```jldoctest
julia> clamp.([pi, 1.0, big(10)], 2.0, 9.0)
3-element Vector{BigFloat}:
 3.141592653589793238462643383279502884197169399375105820974944592307816406286198
 2.0
 9.0

julia> clamp.([11, 8, 5], 10, 6)  # lo > hi인 경우의 예
3-element Vector{Int64}:
  6
  6
 10
```
