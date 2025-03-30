```
abs(x)
```

`x`의 절대값입니다.

`abs`가 부호가 있는 정수에 적용될 때, 오버플로우가 발생할 수 있으며, 이로 인해 음수 값이 반환될 수 있습니다. 이 오버플로우는 `abs`가 부호가 있는 정수의 최소 표현 가능 값에 적용될 때만 발생합니다. 즉, `x == typemin(typeof(x))`일 때, `abs(x) == x < 0`이며, 예상할 수 있는 `-x`가 아닙니다.

참고: [`abs2`](@ref), [`unsigned`](@ref), [`sign`](@ref).

# 예제

```jldoctest
julia> abs(-3)
3

julia> abs(1 + im)
1.4142135623730951

julia> abs.(Int8[-128 -127 -126 0 126 127])  # typemin(Int8)에서 오버플로우
1×6 Matrix{Int8}:
 -128  127  126  0  126  127

julia> maximum(abs, [1, -2, 3, -4])
4
```
