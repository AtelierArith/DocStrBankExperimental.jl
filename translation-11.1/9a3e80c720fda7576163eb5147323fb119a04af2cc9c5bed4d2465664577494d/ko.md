```
eps(x::AbstractFloat)
```

`x`의 *마지막 자리 단위* (ulp)를 반환합니다. 이는 `x`에서 연속적으로 표현 가능한 부동 소수점 값 사이의 거리입니다. 대부분의 경우, `x`의 양쪽 거리 차이가 다르면 두 값 중 더 큰 값을 취합니다. 즉,

```
eps(x) == max(x-prevfloat(x), nextfloat(x)-x)
```

이 규칙의 예외는 가장 작은 및 가장 큰 유한 값들(예: [`Float64`](@ref)에 대한 `nextfloat(-Inf)` 및 `prevfloat(Inf)`)로, 이들은 더 작은 값으로 반올림됩니다.

이 동작의 이유는 `eps`가 부동 소수점 반올림 오류의 경계를 설정하기 때문입니다. 기본 `RoundNearest` 반올림 모드에서, 만약 $y$가 실수이고 $x$가 $y$에 가장 가까운 부동 소수점 수라면,

$$
|y-x| \leq \operatorname{eps}(x)/2.
$$

또한: [`nextfloat`](@ref), [`issubnormal`](@ref), [`floatmax`](@ref).

# 예제

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(prevfloat(2.0))
2.220446049250313e-16

julia> eps(2.0)
4.440892098500626e-16

julia> x = prevfloat(Inf)      # 가장 큰 유한 Float64
1.7976931348623157e308

julia> x + eps(x)/2            # 반올림하여 올림
Inf

julia> x + prevfloat(eps(x)/2) # 반올림하여 내림
1.7976931348623157e308
```
