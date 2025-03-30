```
exponent(x::Real) -> Int
```

절대값 `abs(x)`에 대해 `2^y ≤ abs(x)`를 만족하는 가장 큰 정수 `y`를 반환합니다.

`x`가 0, 무한대 또는 [`NaN`](@ref)일 때 `DomainError`를 발생시킵니다. 다른 비정상 부동 소수점 숫자 `x`에 대해서는, 이는 `x`의 지수 비트에 해당합니다.

또한 [`signbit`](@ref), [`significand`](@ref), [`frexp`](@ref), [`issubnormal`](@ref), [`log2`](@ref), [`ldexp`](@ref)도 참조하세요.

# 예제

```jldoctest
julia> exponent(8)
3

julia> exponent(6.5)
2

julia> exponent(-1//4)
-2

julia> exponent(3.142e-4)
-12

julia> exponent(floatmin(Float32)), exponent(nextfloat(0.0f0))
(-126, -149)

julia> exponent(0.0)
ERROR: DomainError with 0.0:
Cannot be ±0.0.
[...]
```
