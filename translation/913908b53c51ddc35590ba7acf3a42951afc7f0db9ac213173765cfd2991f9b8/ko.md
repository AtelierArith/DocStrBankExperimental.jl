```
round([T,] x, [r::RoundingMode])
round(x, [r::RoundingMode]; digits::Integer=0, base = 10)
round(x, [r::RoundingMode]; sigdigits::Integer, base = 10)
```

숫자 `x`를 반올림합니다.

키워드 인자가 없으면 `x`는 정수 값으로 반올림되며, 제공된 `T`가 없으면 `x`와 동일한 유형의 값을 반환합니다. 값이 `T`로 표현될 수 없는 경우 [`InexactError`](@ref)가 발생합니다. 이는 [`convert`](@ref)와 유사합니다.

`digits` 키워드 인자가 제공되면, 소수점 이하(또는 음수일 경우 소수점 위)의 지정된 자릿수로 반올림합니다. `base`는 10입니다.

`sigdigits` 키워드 인자가 제공되면, 지정된 유효 숫자 수로 반올림합니다. `base`는 10입니다.

[`RoundingMode`](@ref) `r`는 반올림 방향을 제어합니다. 기본값은 [`RoundNearest`](@ref)로, 이는 가장 가까운 정수로 반올림하며, 동점(0.5의 분수 값)은 가장 가까운 짝수 정수로 반올림됩니다. 전역 반올림 모드가 변경되면 `round`가 잘못된 결과를 줄 수 있습니다(자세한 내용은 [`rounding`](@ref) 참조).

부동 소수점 유형으로 반올림할 때, 해당 유형으로 표현 가능한 정수(및 Inf)로 반올림합니다. Inf는 "가장 가까운" 값을 결정하는 데 있어 `floatmax(T)`보다 하나 더 큰 ulp로 처리됩니다. 이는 [`convert`](@ref)와 유사합니다.

# 예제

```jldoctest
julia> round(1.7)
2.0

julia> round(Int, 1.7)
2

julia> round(1.5)
2.0

julia> round(2.5)
2.0

julia> round(pi; digits=2)
3.14

julia> round(pi; digits=3, base=2)
3.125

julia> round(123.456; sigdigits=2)
120.0

julia> round(357.913; sigdigits=4, base=2)
352.0

julia> round(Float16, typemax(UInt128))
Inf16

julia> floor(Float16, typemax(UInt128))
Float16(6.55e4)
```

!!! note
    2가 아닌 진수에서 지정된 자릿수로 반올림할 때, 이진 부동 소수점 숫자에서 작동할 경우 부정확할 수 있습니다. 예를 들어, `1.15`로 표현된 [`Float64`](@ref) 값은 실제로 1.15보다 *작습니다*, 그러나 1.2로 반올림됩니다. 예를 들어:

    ```jldoctest
    julia> x = 1.15
    1.15

    julia> big(1.15)
    1.149999999999999911182158029987476766109466552734375

    julia> x < 115//100
    true

    julia> round(x, digits=1)
    1.2
    ```


# 확장

`round`를 새로운 숫자 유형으로 확장하려면, 일반적으로 `Base.round(x::NewType, r::RoundingMode)`를 정의하는 것으로 충분합니다.
