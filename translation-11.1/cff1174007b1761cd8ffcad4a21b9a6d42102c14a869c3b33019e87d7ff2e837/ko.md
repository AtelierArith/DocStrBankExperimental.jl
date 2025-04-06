```
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]])
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; digits=0, base=10)
round(z::Complex[, RoundingModeReal, [RoundingModeImaginary]]; sigdigits, base=10)
```

복소수 값 `z`에 대해 지정된 [`RoundingMode`](@ref)들을 사용하여 `z`에 가장 가까운 정수 값을 반환합니다. 첫 번째 [`RoundingMode`](@ref)는 실수 구성 요소의 반올림에 사용되며, 두 번째는 허수 구성 요소의 반올림에 사용됩니다.

`RoundingModeReal` 및 `RoundingModeImaginary`는 기본적으로 [`RoundNearest`](@ref)로 설정되어 있으며, 이는 가장 가까운 정수로 반올림하며, 동점(0.5의 분수 값)은 가장 가까운 짝수 정수로 반올림됩니다.

# 예제

```jldoctest
julia> round(3.14 + 4.5im)
3.0 + 4.0im

julia> round(3.14 + 4.5im, RoundUp, RoundNearestTiesUp)
4.0 + 5.0im

julia> round(3.14159 + 4.512im; digits = 1)
3.1 + 4.5im

julia> round(3.14159 + 4.512im; sigdigits = 3)
3.14 + 4.51im
```
