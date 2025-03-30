```
BigFloat(x::Union{Real, AbstractString} [, rounding::RoundingMode=rounding(BigFloat)]; [precision::Integer=precision(BigFloat)])
```

`x`로부터 임의의 정밀도 부동 소수점 숫자를 생성하며, 정밀도는 `precision`입니다. `rounding` 인자는 변환이 정확하게 수행될 수 없는 경우 결과가 반올림되는 방향을 지정합니다. 제공되지 않으면, 현재 전역 값에 의해 설정됩니다.

`BigFloat(x::Real)`은 `convert(BigFloat,x)`와 동일하지만, `x`가 이미 `BigFloat`인 경우 현재 전역 정밀도로 설정된 값을 반환합니다; `convert`는 항상 `x`를 반환합니다.

`BigFloat(x::AbstractString)`은 [`parse`](@ref)와 동일합니다. 이는 소수 리터럴이 파싱될 때 `Float64`로 변환되기 때문에 제공됩니다. 따라서 `BigFloat(2.1)`은 예상한 결과를 제공하지 않을 수 있습니다.

참고:

  * [`@big_str`](@ref)
  * [`rounding`](@ref) 및 [`setrounding`](@ref)
  * [`precision`](@ref) 및 [`setprecision`](@ref)

!!! compat "Julia 1.1"
    `precision`을 키워드 인자로 사용하는 것은 최소한 Julia 1.1이 필요합니다. Julia 1.0에서는 `precision`이 두 번째 위치 인자입니다 (`BigFloat(x, precision)`).


# 예제

```jldoctest
julia> BigFloat(2.1) # 여기서 2.1은 Float64입니다.
2.100000000000000088817841970012523233890533447265625

julia> BigFloat("2.1") # 2.1에 가장 가까운 BigFloat
2.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> BigFloat("2.1", RoundUp)
2.100000000000000000000000000000000000000000000000000000000000000000000000000021

julia> BigFloat("2.1", RoundUp, precision=128)
2.100000000000000000000000000000000000007
```
