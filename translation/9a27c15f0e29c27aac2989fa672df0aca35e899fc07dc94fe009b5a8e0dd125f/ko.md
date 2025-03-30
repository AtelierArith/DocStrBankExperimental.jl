```
log1p(x)
```

정확한 자연 로그 `1+x`의 값. [`Real`](@ref) 인수가 -1보다 작은 경우 [`DomainError`](@ref)를 발생시킵니다.

# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log1p(-0.5)
-0.6931471805599453

julia> log1p(0)
0.0

julia> log1p(-2)
ERROR: DomainError with -2.0:
log1p는 -1보다 작은 실수 인수로 호출되었지만 복소수 인수로 호출될 경우에만 복소수 결과를 반환합니다. log1p(Complex(x))를 시도해 보세요.
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```
