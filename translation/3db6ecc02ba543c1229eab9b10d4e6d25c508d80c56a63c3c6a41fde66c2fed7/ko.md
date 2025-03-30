```
DateTime(f::Function, y[, m, d, h, mi, s]; step=Day(1), limit=10000) -> DateTime
```

조정기 API를 통해 `DateTime`을 생성합니다. 시작점은 제공된 `y, m, d...` 인수로 구성되며, `f::Function`이 `true`를 반환할 때까지 조정됩니다. 조정 시의 단계 크기는 `step` 키워드를 통해 수동으로 제공할 수 있습니다. `limit`는 조정 API가 오류를 발생시키기 전에 추구할 최대 반복 횟수의 한계를 제공합니다(만약 `f::Function`이 결코 만족되지 않는 경우).

# 예제

```jldoctest
julia> DateTime(dt -> second(dt) == 40, 2010, 10, 20, 10; step = Second(1))
2010-10-20T10:00:40

julia> DateTime(dt -> hour(dt) == 20, 2010, 10, 20, 10; step = Hour(1), limit = 5)
ERROR: ArgumentError: Adjustment limit reached: 5 iterations
Stacktrace:
[...]
```
