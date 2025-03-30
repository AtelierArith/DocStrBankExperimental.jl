```
randn!([rng=default_rng()], A::AbstractArray) -> A
```

배열 `A`를 정규 분포(평균 0, 표준 편차 1)를 따르는 난수로 채웁니다. [`rand`](@ref) 함수도 참조하세요.

# 예제

```jldoctest
julia> randn!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 -0.6457306721039767
 -1.4632513788889214
 -1.6236037455860806
 -0.21766510678354617
  0.4922456865251828
```
