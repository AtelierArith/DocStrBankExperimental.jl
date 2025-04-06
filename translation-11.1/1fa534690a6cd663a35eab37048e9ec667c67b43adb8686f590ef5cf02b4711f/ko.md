```
log2(x)
```

`x`의 밑이 2인 로그를 계산합니다. 음수 [`Real`](@ref) 인수에 대해 [`DomainError`](@ref)를 발생시킵니다.

참고: [`exp2`](@ref), [`ldexp`](@ref), [`ispow2`](@ref).

# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log2(4)
2.0

julia> log2(10)
3.321928094887362

julia> log2(-2)
ERROR: DomainError with -2.0:
log2는 음수 실수 인수로 호출되었지만 복소수 인수로 호출될 경우에만 복소수 결과를 반환합니다. log2(Complex(x))를 시도해 보세요.
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]

julia> log2.(2.0 .^ (-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```
