```
Date(f::Function, y[, m, d]; step=Day(1), limit=10000) -> Date
```

조정기 API를 통해 `Date`를 생성합니다. 시작점은 제공된 `y, m, d` 인수로 구성되며, `f::Function`이 `true`를 반환할 때까지 조정됩니다. 조정 시의 단계 크기는 `step` 키워드를 통해 수동으로 제공할 수 있습니다. `limit`는 조정 API가 오류를 발생시키기 전에 추구할 최대 반복 횟수의 한계를 제공합니다(주어진 `f::Function`이 결코 만족되지 않는 경우).

# 예제

```jldoctest
julia> Date(date -> week(date) == 20, 2010, 01, 01)
2010-05-17

julia> Date(date -> year(date) == 2010, 2000, 01, 01)
2010-01-01

julia> Date(date -> month(date) == 10, 2000, 01, 01; limit = 5)
ERROR: ArgumentError: Adjustment limit reached: 5 iterations
Stacktrace:
[...]
```
