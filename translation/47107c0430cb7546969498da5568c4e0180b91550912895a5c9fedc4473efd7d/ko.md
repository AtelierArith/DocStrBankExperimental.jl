```
log(x)
```

`x`의 자연 로그를 계산합니다.

음수 [`Real`](@ref) 인수에 대해 [`DomainError`](@ref)를 발생시킵니다. 복소수 인수를 사용하여 복소수 결과를 얻으십시오. 음의 실축을 따라 분기 절단이 있으며, 이때 `-0.0im`은 축 아래에 있는 것으로 간주됩니다.

또한 [`ℯ`](@ref), [`log1p`](@ref), [`log2`](@ref), [`log10`](@ref)를 참조하십시오.

# 예제

```jldoctest; filter = r"Stacktrace:(\n \[[0-9]+\].*)*"
julia> log(2)
0.6931471805599453

julia> log(-3)
ERROR: DomainError with -3.0:
log은 음의 실수 인수로 호출되었지만 복소수 인수로 호출될 경우에만 복소수 결과를 반환합니다. log(Complex(x))를 시도하십시오.
Stacktrace:
 [1] throw_complex_domainerror(::Symbol, ::Float64) at ./math.jl:31
[...]

julia> log(-3 + 0im)
1.0986122886681098 + 3.141592653589793im

julia> log(-3 - 0.0im)
1.0986122886681098 - 3.141592653589793im

julia> log.(exp.(-1:1))
3-element Vector{Float64}:
 -1.0
  0.0
  1.0
```
