```
함수(f::Function, h, mi=0; step::Period=Second(1), limit::Int=10000)
함수(f::Function, h, mi, s; step::Period=Millisecond(1), limit::Int=10000)
함수(f::Function, h, mi, s, ms; step::Period=Microsecond(1), limit::Int=10000)
함수(f::Function, h, mi, s, ms, us; step::Period=Nanosecond(1), limit::Int=10000)
```

조정기 API를 통해 `Time`을 생성합니다. 시작점은 제공된 `h, mi, s, ms, us` 인수로 구성되며, `f::Function`이 `true`를 반환할 때까지 조정됩니다. 조정 시의 단계 크기는 `step` 키워드를 통해 수동으로 제공할 수 있습니다. `limit`는 조정 API가 오류를 발생시키기 전에 추구할 최대 반복 횟수의 한계를 제공합니다(즉, `f::Function`이 결코 만족되지 않는 경우). 주의할 점은 기본 단계가 주어진 인수에 대해 더 높은 정밀도를 허용하도록 조정된다는 것입니다. 즉, 시간, 분, 초 인수가 제공되면 기본 단계는 `Second(1)` 대신 `Millisecond(1)`이 됩니다.

# 예제

```jldoctest
julia> Time(t -> minute(t) == 30, 20)
20:30:00

julia> Time(t -> minute(t) == 0, 20)
20:00:00

julia> Time(t -> hour(t) == 10, 3; limit = 5)
ERROR: ArgumentError: Adjustment limit reached: 5 iterations
Stacktrace:
[...]
```
