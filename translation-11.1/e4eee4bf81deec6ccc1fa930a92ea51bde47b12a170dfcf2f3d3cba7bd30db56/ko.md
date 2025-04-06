```
randexp!([rng=default_rng()], A::AbstractArray) -> A
```

배열 `A`를 스케일 1인 지수 분포를 따르는 랜덤 숫자로 채웁니다.

# 예시

```jldoctest
julia> randexp!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 1.1757716836348473
 1.758884569451514
 1.0083623637301151
 0.3510644315565272
 0.6348266443720407
```
