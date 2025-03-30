```
isapprox(x, y; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps, nans::Bool=false[, norm::Function])
```

부정확한 동등성 비교. 두 숫자는 상대적 거리 *또는* 절대적 거리가 허용 오차 범위 내에 있을 경우 동등하다고 비교됩니다: `isapprox`는 `norm(x-y) <= max(atol, rtol*max(norm(x), norm(y)))`일 때 `true`를 반환합니다. 기본 `atol`(절대 허용 오차)은 0이며 기본 `rtol`(상대 허용 오차)은 `x`와 `y`의 유형에 따라 달라집니다. 키워드 인수 `nans`는 NaN 값이 동등한 것으로 간주되는지 여부를 결정합니다(기본값은 false).

실수 또는 복소수 부동 소수점 값의 경우, `atol > 0`이 지정되지 않으면 `rtol`은 `x` 또는 `y`의 유형 중 더 큰 값의 [`eps`](@ref)의 제곱근으로 기본 설정됩니다(가장 정밀도가 낮음). 이는 약 절반의 유효 숫자의 동등성을 요구하는 것에 해당합니다. 그렇지 않은 경우, 예를 들어 정수 인수의 경우 또는 `atol > 0`이 제공된 경우 `rtol`은 기본값이 0입니다.

`norm` 키워드는 숫자 `(x,y)`에 대해 기본적으로 `abs`로 설정되며, 배열에 대해서는 `LinearAlgebra.norm`으로 설정됩니다(대체 `norm` 선택이 때때로 유용할 수 있습니다). `x`와 `y`가 배열인 경우, `norm(x-y)`가 유한하지 않으면(즉, `±Inf` 또는 `NaN`), 비교는 `x`와 `y`의 모든 요소가 구성 요소별로 대략 동등한지 확인하는 것으로 되돌아갑니다.

이진 연산자 `≈`는 기본 인수로 `isapprox`와 동일하며, `x ≉ y`는 `!isapprox(x,y)`와 동일합니다.

`x ≈ 0`(즉, 기본 허용 오차로 0과 비교하는 것)은 기본 `atol`이 `0`이므로 `x == 0`과 동일합니다. 이러한 경우 적절한 `atol`을 제공하거나(또는 `norm(x) ≤ atol`을 사용) 코드를 재배치해야 합니다(예: `x ≈ y`를 사용하기보다는 `x - y ≈ 0`을 사용). 비제로 `atol`을 자동으로 선택하는 것은 불가능합니다. 이는 문제의 전체 스케일링(즉, "단위")에 따라 달라지기 때문입니다: 예를 들어, `x - y ≈ 0`에서 `atol=1e-9`는 `x`가 미터 단위의 [지구의 반지름](https://en.wikipedia.org/wiki/Earth_radius)일 경우 터무니없이 작은 허용 오차이지만, `x`가 미터 단위의 [수소 원자의 반지름](https://en.wikipedia.org/wiki/Bohr_radius)일 경우 터무니없이 큰 허용 오차입니다.

!!! compat "Julia 1.6"
    숫자(비배열) 인수를 비교할 때 `norm` 키워드 인수를 전달하려면 Julia 1.6 이상이 필요합니다.


# 예제

```jldoctest
julia> isapprox(0.1, 0.15; atol=0.05)
true

julia> isapprox(0.1, 0.15; rtol=0.34)
true

julia> isapprox(0.1, 0.15; rtol=0.33)
false

julia> 0.1 + 1e-10 ≈ 0.1
true

julia> 1e-10 ≈ 0
false

julia> isapprox(1e-10, 0, atol=1e-8)
true

julia> isapprox([10.0^9, 1.0], [10.0^9, 2.0]) # using `norm`
true
```
