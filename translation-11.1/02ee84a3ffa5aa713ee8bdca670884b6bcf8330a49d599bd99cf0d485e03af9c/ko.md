```
log10(x)
```

`x`의 10을 밑으로 하는 로그를 계산합니다. 음수 [`Real`](@ref) 인수에 대해 [`DomainError`](@ref)를 발생시킵니다.

# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log10(100)
2.0

julia> log10(2)
0.3010299956639812

julia> log10(-2)
ERROR: DomainError with -2.0:
log10은 음수 실수 인수로 호출되었지만 복소수 인수로 호출될 경우에만 복소수 결과를 반환합니다. log10(Complex(x))를 시도해 보세요.
Stacktrace:
 [1] throw_complex_domainerror(f::Symbol, x::Float64) at ./math.jl:31
[...]
```
