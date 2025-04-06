```
rem2pi(x, r::RoundingMode)
```

`x`를 `2π`로 정수 나눈 나머지를 계산하며, 몫은 반올림 모드 `r`에 따라 반올림됩니다. 즉, 다음과 같은 양입니다.

```
x - 2π*round(x/(2π),r)
```

중간 반올림 없이 계산됩니다. 내부적으로 2π의 고정밀 근사를 사용하므로 `rem(x,2π,r)`보다 더 정확한 결과를 제공합니다.

  * `r == RoundNearest`인 경우, 결과는 구간 $[-π, π]$에 있습니다. 일반적으로 가장 정확한 결과입니다. [`RoundNearest`](@ref)도 참조하십시오.
  * `r == RoundToZero`인 경우, 결과는 `x`가 양수일 때 구간 $[0, 2π]$에 있으며, 그렇지 않으면 구간 $[-2π, 0]$에 있습니다. [`RoundToZero`](@ref)도 참조하십시오.
  * `r == RoundDown`인 경우, 결과는 구간 $[0, 2π]$에 있습니다. [`RoundDown`](@ref)도 참조하십시오.
  * `r == RoundUp`인 경우, 결과는 구간 $[-2π, 0]$에 있습니다. [`RoundUp`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> rem2pi(7pi/4, RoundNearest)
-0.7853981633974485

julia> rem2pi(7pi/4, RoundDown)
5.497787143782138
```
