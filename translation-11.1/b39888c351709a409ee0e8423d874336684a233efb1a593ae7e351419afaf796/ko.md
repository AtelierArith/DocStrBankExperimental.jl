```
rem(x, y, r::RoundingMode=RoundToZero)
```

`y`로 정수 나눗셈을 한 후 `x`의 나머지를 계산하며, 몫은 반올림 모드 `r`에 따라 반올림됩니다. 즉, 다음과 같은 양입니다.

```
x - y * round(x / y, r)
```

중간 반올림 없이.

  * `r == RoundNearest`인 경우, 결과는 정확하며 구간 $[-|y| / 2, |y| / 2]$에 있습니다. [`RoundNearest`](@ref)를 참조하십시오.
  * `r == RoundToZero`(기본값)인 경우, 결과는 정확하며 `x`가 양수일 때 구간 $[0, |y|)$에, 그렇지 않으면 $(-|y|, 0]$에 있습니다. [`RoundToZero`](@ref)를 참조하십시오.
  * `r == RoundDown`인 경우, 결과는 `y`가 양수일 때 구간 $[0, y)$에, 그렇지 않으면 $(y, 0]$에 있습니다. `x`와 `y`의 부호가 다르고 `abs(x) < abs(y)`인 경우 결과가 정확하지 않을 수 있습니다. [`RoundDown`](@ref)를 참조하십시오.
  * `r == RoundUp`인 경우, 결과는 `y`가 양수일 때 구간 $(-y, 0]$에, 그렇지 않으면 $[0, -y)$에 있습니다. `x`와 `y`의 부호가 같고 `abs(x) < abs(y)`인 경우 결과가 정확하지 않을 수 있습니다. [`RoundUp`](@ref)를 참조하십시오.
  * `r == RoundFromZero`인 경우, 결과는 `y`가 양수일 때 구간 $(-y, 0]$에, 그렇지 않으면 $[0, -y)$에 있습니다. `x`와 `y`의 부호가 같고 `abs(x) < abs(y)`인 경우 결과가 정확하지 않을 수 있습니다. [`RoundFromZero`](@ref)를 참조하십시오.

!!! compat "Julia 1.9"
    `RoundFromZero`는 최소한 Julia 1.9가 필요합니다.


# 예제:

```jldoctest
julia> x = 9; y = 4;

julia> x % y  # rem(x, y)와 동일
1

julia> x ÷ y  # div(x, y)와 동일
2

julia> x == div(x, y) * y + rem(x, y)
true
```
