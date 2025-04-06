```
rem(x, y)
%(x, y)
```

유클리드 나눗셈에서의 나머지로, `x`와 같은 부호를 가지며 `y`보다 크기가 작은 값을 반환합니다. 이 값은 항상 정확합니다.

참고: [`div`](@ref), [`mod`](@ref), [`mod1`](@ref), [`divrem`](@ref).

# 예제

```jldoctest
julia> x = 15; y = 4;

julia> x % y
3

julia> x == div(x, y) * y + rem(x, y)
true

julia> rem.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -2  -1  0  -2  -1  0  1  2  0  1  2
```
