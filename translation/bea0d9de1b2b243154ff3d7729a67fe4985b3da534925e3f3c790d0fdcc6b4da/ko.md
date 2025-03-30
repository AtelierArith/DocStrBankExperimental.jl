```
LogRange{T}(start, stop, len) <: AbstractVector{T}
```

`start`와 `stop` 사이에 로그적으로 간격이 있는 요소를 가진 범위로, 간격은 `len`에 의해 조절됩니다. [`logrange`](@ref)에 의해 반환됩니다.

[`LinRange`](@ref)와 마찬가지로, 첫 번째 및 마지막 요소는 제공된 값과 정확히 일치하지만, 중간 값은 작은 부동 소수점 오류가 있을 수 있습니다. 이러한 값은 생성 시 저장된 끝점의 로그를 사용하여 계산되며, 종종 `T`보다 더 높은 정밀도로 저장됩니다.

# 예제

```jldoctest
julia> logrange(1, 4, length=5)
5-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 1.0, 1.41421, 2.0, 2.82843, 4.0

julia> Base.LogRange{Float16}(1, 4, 5)
5-element Base.LogRange{Float16, Float64}:
 1.0, 1.414, 2.0, 2.828, 4.0

julia> logrange(1e-310, 1e-300, 11)[1:2:end]
6-element Vector{Float64}:
 1.0e-310
 9.999999999999974e-309
 9.999999999999981e-307
 9.999999999999988e-305
 9.999999999999994e-303
 1.0e-300

julia> prevfloat(1e-308, 5) == ans[2]
true
```

정수 eltype `T`는 허용되지 않습니다. 예를 들어 `round.(Int, xs)`를 사용하거나 일부 정수 기반의 명시적인 거듭제곱을 사용하십시오:

```jldoctest
julia> xs = logrange(1, 512, 4)
4-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 1.0, 8.0, 64.0, 512.0

julia> 2 .^ (0:3:9) |> println
[1, 8, 64, 512]
```

!!! compat "Julia 1.11"
    이 유형은 최소한 Julia 1.11이 필요합니다.

