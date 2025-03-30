```
sqrt(x)
```

Return $\sqrt{x}$.

음수 [`Real`](@ref) 인수에 대해 [`DomainError`](@ref)를 발생시킵니다. 대신 복소수 음수 인수를 사용하세요. `sqrt`는 음의 실수 축을 따라 분기 절단이 있음을 유의하세요.

접두사 연산자 `√`는 `sqrt`와 동일합니다.

참고: [`hypot`](@ref).

# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> sqrt(big(81))
9.0

julia> sqrt(big(-81))
ERROR: DomainError with -81.0:
NaN result for non-NaN input.
Stacktrace:
 [1] sqrt(::BigFloat) at ./mpfr.jl:501
[...]

julia> sqrt(big(complex(-81)))
0.0 + 9.0im

julia> sqrt(-81 - 0.0im)  # -0.0im은 분기 절단 아래에 있습니다
0.0 - 9.0im

julia> .√(1:4)
4-element Vector{Float64}:
 1.0
 1.4142135623730951
 1.7320508075688772
 2.0
```
