```
logrange(start, stop, length)
logrange(start, stop; length)
```

주어진 끝점 사이에 로그적으로 간격이 있는 요소로 구성된 특수 배열을 만듭니다. 즉, 연속 요소의 비율은 길이에서 계산된 상수입니다.

이는 Python의 `geomspace`와 유사합니다. Mathematica의 `PowerRange`와는 달리, 비율이 아니라 요소의 수를 지정합니다. Python 및 Matlab의 `logspace`와는 달리, `start` 및 `stop` 인수는 항상 결과의 첫 번째 및 마지막 요소이며, 어떤 기본에 적용된 거듭제곱이 아닙니다.

# 예제

```jldoctest
julia> logrange(10, 4000, length=3)
3-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 10.0, 200.0, 4000.0

julia> ans[2] ≈ sqrt(10 * 4000)  # 중간 요소는 기하 평균
true

julia> range(10, 40, length=3)[2] ≈ (10 + 40)/2  # 산술 평균
true

julia> logrange(1f0, 32f0, 11)
11-element Base.LogRange{Float32, Float64}:
 1.0, 1.41421, 2.0, 2.82843, 4.0, 5.65685, 8.0, 11.3137, 16.0, 22.6274, 32.0

julia> logrange(1, 1000, length=4) ≈ 10 .^ (0:3)
true
```

자세한 내용은 [`LogRange`](@ref Base.LogRange) 유형을 참조하십시오.

선형 간격의 점에 대해서는 [`range`](@ref)도 참조하십시오.

!!! compat "Julia 1.11"
    이 함수는 최소한 Julia 1.11이 필요합니다.

