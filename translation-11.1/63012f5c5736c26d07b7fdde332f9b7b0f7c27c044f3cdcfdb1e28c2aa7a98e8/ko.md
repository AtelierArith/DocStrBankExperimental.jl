```
tonext(func::Function, dt::TimeType; step=Day(1), limit=10000, same=false) -> TimeType
```

`dt`를 조정하여 `func`가 `true`를 반환할 때까지 최대 `limit` 반복을 `step` 증가로 수행합니다. `func`는 단일 `TimeType` 인수를 받아야 하며 [`Bool`](@ref)를 반환해야 합니다. `same`은 `dt`가 `func`를 만족하는 데 고려될 수 있도록 허용합니다.
