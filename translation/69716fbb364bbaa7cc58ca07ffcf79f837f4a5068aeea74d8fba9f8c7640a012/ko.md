```
abs2(x)
```

`x`의 제곱 절대값입니다.

이는 특히 `abs(x)`가 [`hypot`](@ref)를 통해 제곱근을 요구하는 복소수의 경우 `abs(x)^2`보다 더 빠를 수 있습니다.

또한 [`abs`](@ref), [`conj`](@ref), [`real`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> abs2(-3)
9

julia> abs2(3.0 + 4.0im)
25.0

julia> sum(abs2, [1+2im, 3+4im])  # LinearAlgebra.norm(x)^2
30
```
