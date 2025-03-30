```
log(b,x)
```

`x`의 밑 `b` 로그를 계산합니다. 음수 [`Real`](@ref) 인수에 대해 [`DomainError`](@ref)를 발생시킵니다.

# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(4,8)
1.5

julia> log(4,2)
0.5

julia> log(-2, 3)
ERROR: DomainError with -2.0:
log는 음수 실수 인수로 호출되었지만 복소수 인수로 호출될 경우에만 복소수 결과를 반환합니다. log(Complex(x))를 시도해 보세요.
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(2, -3)
ERROR: DomainError with -3.0:
log는 음수 실수 인수로 호출되었지만 복소수 인수로 호출될 경우에만 복소수 결과를 반환합니다. log(Complex(x))를 시도해 보세요.
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]
```

!!! 주의     `b`가 2 또는 10의 거듭제곱인 경우, [`log2`](@ref) 또는 [`log10`](@ref)를 사용해야 합니다. 이러한 함수는 일반적으로 더 빠르고 더 정확합니다. 예를 들어,

````
```jldoctest
julia> log(100,1000000)
2.9999999999999996

julia> log10(1000000)/2
3.0
```
````
