```
significand(x)
```

부동 소수점 수의 유효 숫자(즉, 맨티사)를 추출합니다. 만약 `x`가 0이 아닌 유한한 수라면, 결과는 `x`와 같은 유형과 부호를 가지며 절대값이 $[1,2)$ 구간에 있는 수가 됩니다. 그렇지 않으면 `x`가 반환됩니다.

또한 [`frexp`](@ref), [`exponent`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> significand(15.2)
1.9

julia> significand(-15.2)
-1.9

julia> significand(-15.2) * 2^3
-15.2

julia> significand(-Inf), significand(Inf), significand(NaN)
(-Inf, Inf, NaN)
```
